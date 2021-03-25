# Darknet simplified for NixOS
### Motivation of this fork:
- simplifying the installation of darknet for NixOS users
- creating a simple demonstration enviroment -> being executable with a few commands

### Implementation:
- I created a default.nix, compilying the needed dependencies in a way darknet supports NVIDIA CUDA
- Our CI CD server builds it on a daily basis -> we are able to use it quicker

### Guide:
```bash
# clone the repository
git clone https://github.com/MayNiklas/darknet.git && cd darknet

# allow unfree (NVIDIA CUDA)
export NIXPKGS_ALLOW_UNFREE=1

# build darknet with all needed dependency correctly configured
nix-build -E 'with import <nixpkgs> {}; callPackage ./default.nix {}' -v

# download yolov3-tiny.weights, a tiny pre trained modell we can use for demo purposes
wget https://pjreddie.com/media/files/yolov3-tiny.weights -P  cfg/

# execute darknet in detector mode
./result/bin/darknet ./darknet detector demo cfg/coco.data cfg/yolov3-tiny.cfg cfg/yolov3-tiny.weights
```
I recommend checking out nvtop for monitoring your GPU usage. Tiny modells shouldn't really need much ressources. Bigger models quickly need 15GB+ VRAM.
The rest of the repository stays unchanged!


![Darknet Logo](http://pjreddie.com/media/files/darknet-black-small.png)

# Darknet #
Darknet is an open source neural network framework written in C and CUDA. It is fast, easy to install, and supports CPU and GPU computation.

**Discord** invite link for for communication and questions: https://discord.gg/zSq8rtW

## Scaled-YOLOv4: 

* **paper:** https://arxiv.org/abs/2011.08036

* **source code - Pytorch (use to reproduce results):** https://github.com/WongKinYiu/ScaledYOLOv4

* **source code - Darknet:** https://github.com/AlexeyAB/darknet

* **Medium:** https://alexeyab84.medium.com/scaled-yolo-v4-is-the-best-neural-network-for-object-detection-on-ms-coco-dataset-39dfa22fa982?source=friends_link&sk=c8553bfed861b1a7932f739d26f487c8

## YOLOv4:

* **paper:** https://arxiv.org/abs/2004.10934

* **source code:** https://github.com/AlexeyAB/darknet

* **Wiki:** https://github.com/AlexeyAB/darknet/wiki

* **useful links:** https://medium.com/@alexeyab84/yolov4-the-most-accurate-real-time-neural-network-on-ms-coco-dataset-73adfd3602fe?source=friends_link&sk=6039748846bbcf1d960c3061542591d7

For more information see the [Darknet project website](http://pjreddie.com/darknet).

For questions or issues please use the [Google Group](https://groups.google.com/forum/#!forum/darknet).

![scaled_yolov4](https://user-images.githubusercontent.com/4096485/101356322-f1f5a180-38a8-11eb-9907-4fe4f188d887.png) AP50:95 - FPS (Tesla V100) Paper: https://arxiv.org/abs/2011.08036

----

![YOLOv4Tiny](https://user-images.githubusercontent.com/4096485/101363015-e5c21200-38b1-11eb-986f-b3e516e05977.png)

----

![YOLOv4](https://user-images.githubusercontent.com/4096485/90338826-06114c80-dff5-11ea-9ba2-8eb63a7409b3.png)


----

![OpenCV_TRT](https://user-images.githubusercontent.com/4096485/90338805-e5e18d80-dff4-11ea-8a68-5710956256ff.png)
