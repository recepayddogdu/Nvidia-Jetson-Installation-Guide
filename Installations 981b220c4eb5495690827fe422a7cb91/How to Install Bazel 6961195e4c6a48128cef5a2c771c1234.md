# How to Install Bazel?

In this blog-post, we will install Bazel on Jetson. First, we will download bazelisk-linux-arm64 file from github bazelisk library. Then, we will install it.

Below steps show installation of bazelisk v1.8.1, but you can install any desired version from [https://github.com/bazelbuild/bazelisk/releases](https://github.com/bazelbuild/bazelisk/releases) using same steps.

## **Downloading Bazel**

First, download bazeliks-linux-arm64 file using wget command.

`wget https://github.com/bazelbuild/bazelisk/releases/download/v1.8.1/bazelisk-linux-arm64`

![https://ucarecdn.com/4d37ee8f-73b9-41b3-b13e-96c95e0728b1/-/format/auto/-/preview/1024x1024/-/quality/lighter/1.png](https://ucarecdn.com/4d37ee8f-73b9-41b3-b13e-96c95e0728b1/-/format/auto/-/preview/1024x1024/-/quality/lighter/1.png)

## **Installing Bazel**

Change file’s privileges to executable using below command.

`chmod +x bazelisk-linux-arm64`

![https://ucarecdn.com/d61ec74d-c14e-4ceb-94d8-1a969dc3db55/-/format/auto/-/preview/1024x1024/-/quality/lighter/2.png](https://ucarecdn.com/d61ec74d-c14e-4ceb-94d8-1a969dc3db55/-/format/auto/-/preview/1024x1024/-/quality/lighter/2.png)

Then, move the file to the directory and change its name to bazel using below command.

`sudo mv bazelisk-linux-arm64 /usr/local/bin/bazel`

![https://ucarecdn.com/91b4d1a1-d0a2-4353-8efb-12a480388b58/-/format/auto/-/preview/1024x1024/-/quality/lighter/3.png](https://ucarecdn.com/91b4d1a1-d0a2-4353-8efb-12a480388b58/-/format/auto/-/preview/1024x1024/-/quality/lighter/3.png)

Finally, make sure you get the binary available in $PATH.

`which bazel`

![https://ucarecdn.com/0f1240ca-0616-4690-bcda-8832fe113853/-/format/auto/-/preview/1024x1024/-/quality/lighter/4.png](https://ucarecdn.com/0f1240ca-0616-4690-bcda-8832fe113853/-/format/auto/-/preview/1024x1024/-/quality/lighter/4.png)

As you can see that the Bazel integrated to the system successfully.

### Source

[How to Install Bazel?](https://www.forecr.io/blogs/installation/how-to-install-bazel)