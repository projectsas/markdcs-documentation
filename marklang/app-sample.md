# App Sample

```text
module app;

using io.Logger;
using logic.Gate;
using logic.Sampler;
using logic.Counter;
using util.Timer;
using util.Starter;

main {
	Starter start;
	Timer t1(200, 0, 0);
	Timer t2(200, 0, 0);
	Gate g;
	Counter ctr;
	Sampler sample(8);
	Logger log("Processed events (in 200ms): %d (x3)\n");
	start.out -> t1.start;
	t1.out -> t2.start;
	t1.out -> g.open;
	t1.out -> ctr.reset;
	t2.out -> t1.start;
	t2.out -> g.close;
	t2.out -> ctr.read;
	t2.out -> sample.clock;
	g.out -> ctr.increment;
	ctr.out -> g.data;
	ctr.out -> sample.data;
	sample.out -> log.in[0];
}
```

