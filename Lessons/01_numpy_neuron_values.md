# Lesson 01 — NumPy array-কে neuron state হিসেবে দেখা

## আজকের লক্ষ্য

NumPy array বানানো, element access করা, threshold দিয়ে কোন neuron spike করবে তা নির্ধারণ করা। আজকের threshold check একটি সরলীকরণ: বাস্তব LIF neuron-এ voltage সময়ের সাথে জমে, তারপর threshold পেরোলে spike হয়।

## ধারণা

একটি array-কে কয়েকটি neuron's membrane voltage হিসেবে ধরো। যেমন `[0.2, 0.7, 0.4]` হলো তিনটি neuron-এর voltage। `threshold = 0.6` হলে দ্বিতীয় neuron threshold পেরিয়েছে। NumPy-র তুলনা `voltage >= threshold` প্রতিটি element-এর জন্য True/False দেয়।

## কোড

```python
import numpy as np

voltage = np.array([0.2, 0.7, 0.4])
threshold = 0.6
spikes = voltage >= threshold

print("Voltage:", voltage)
print("Spike flags:", spikes)
print("Spiking neuron indices:", np.where(spikes)[0])
```

সম্ভাব্য output:

```text
Voltage: [0.2 0.7 0.4]
Spike flags: [False  True False]
Spiking neuron indices: [1]
```

Python index শূন্য থেকে শুরু হয়, তাই `1` মানে দ্বিতীয় neuron।

## নিজে করো

1. চারটি voltage দিয়ে array বানাও: `[0.1, 0.5, 0.8, 0.6]`।
2. threshold `0.5` রাখো। কোন কোন index spike করবে বের করো।
3. `voltage[2]` print করে দেখো।
4. `voltage.mean()` এবং `voltage.shape` কী দেয়, লিখে রাখো।

## ভাবার প্রশ্ন

Threshold-এর সমান voltage-কে spike ধরতে `>=` কেন ব্যবহার করেছি? `>` করলে কোন neuron-এর ফল বদলাবে?

পরের পাঠে voltage-কে শুধু পরীক্ষা না করে input যোগ করে কীভাবে threshold-এর দিকে এগোয়, তা করব—তারপর LIF-এর leak/reset যোগ করব।
