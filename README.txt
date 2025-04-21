## Run e/ docker

docker run 
-d  // detached
--rm // remove when finished
-p 3000:80 // port forward 3000 locally to 80 in the container
--name feedback-app // w/ container name
-v feedback:/app/feedback  // with feedback named volume for persisted feedback data
-v "$(pwd):/app:ro"  // w/ a read only bindmount tieing your local work to the images src
-v /app/node_modules // but don't overwrite the node modules since we npm install in the image 
-v /app/temp // and make sure the read only image doesn't include /app/temp since then we can't save files in the container.
feedback-node:volumes // using image named feedback-node w/ tag volumes.