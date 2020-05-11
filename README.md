# spring-jaeger-minimum

1. Client Lib:
  <dependency>
			<groupId>io.opentracing.contrib</groupId>
			<artifactId>opentracing-spring-jaeger-cloud-starter</artifactId>
			<version>2.0.3</version>
		</dependency>

2. appliction.properties
  spring.application.name=sample_application
  opentracing.jaeger.service-name=sample_application
  opentracing.jaeger.log-spans=true
  opentracing.jaeger.const-sampler.decision=true
   #UDP packets
  opentracing.jaeger.udp-sender.host=192.x.1.x
  opentracing.jaeger.udp-sender.port=6831
  
3. Baggage and tag
  	@Autowired
	  private io.opentracing.Tracer tracer;
  
    tracer.activeSpan().setBaggageItem("x-baggage-correlation-id", UUID.randomUUID().toString());
		tracer.activeSpan().setTag("x-tag-correlation-id", UUID.randomUUID().toString());
