# CS294

Steps that worked (MuJoCo)

1. Try create conda env from file

    $ conda env create -f environment.yml

2. or


        ~$ more ~/.condarc
        channels:
          - intel
          - defaults
        show_channel_urls: true


        conda create -n mujoco intelpython3_full python=**3.5.2**

3. Then `source activate mujoco`

4. pip uninstall cython

5. pip install 'Cython>=0.27.2'

6. brew install gcc --without-multilib

7. unpack MuJoCo like this

        ~$ tree -L 2 .mujoco/
        .mujoco/
        └── mjpro150
            ├── bin
            ├── doc
            ├── include
            ├── model
            └── sample

8. put mjkey.txt to ~/.mujoco

9. install MuJoCo to conda environment

        pip install 'mujoco-py<1.50.2,>=1.50.1'

10. this should work

        $ ipython
        import mujoco_py
        from os.path import dirname
        model = mujoco_py.load_model_from_path("path-to-mujoco-py-checkout/xmls/claw.xml")
        sim = mujoco_py.MjSim(model)

        print(sim.data.qpos)
        # [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]

        sim.step()
        print(sim.data.qpos)
        # [  2.09217903e-06  -1.82329050e-12  -1.16711384e-07  -4.69613872e-11
        #   -1.43931860e-05   4.73350204e-10  -3.23749942e-05  -1.19854057e-13
        #   -2.39251380e-08  -4.46750545e-07   1.78771599e-09  -1.04232280e-08]

11. [Intel Optimized Tensorflow Wheel Now Available](https://software.intel.com/en-us/articles/intel-optimized-tensorflow-wheel-now-available) on Ubuntu

12. until this get fixed https://github.com/openai/mujoco-py/issues/80 do 

        $ cd path-to-gym
        $ git remote add lobachevzky git@github.com:lobachevzky/gym.git
        $ git fetch lobachevzky
        $ git merge lobachevzky/master

    https://github.com/openai/gym/issues/638

    https://github.com/openai/gym/pull/767/files#diff-3f48026043ba85dc635adababe52094cL12

13. intall Gym

        $ pip install -e .

14. `hw1 (master)$ bash demo.bash` should work now
