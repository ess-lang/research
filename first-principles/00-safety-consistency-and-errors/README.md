# Safety, consistency, and errors

## Principle

When feasible, ESS should provide build-time errors for input that will result in behavior the developer does not expect

## Motivation

I think pretty much anyone with experience writing CSS will possess awareness of its lack of "errors". This perception may not be explicitly realized, but nonetheless there will be some intuitive understanding and associated sentiments of confusion and frustration. This notion is discussed in the following talks:

[Understanding style - Matthew Griffith - Elm Europe 2017](https://youtu.be/NYb2GDWMIm0?t=248)

> But what does it mean to break in style? We don't have "undefined is not a function" in style. But we can feel it's broken. An error in style is the unexpected. Anything that's unexpected - we kind of got to consider that an error. That's a bit of loose definition but it's kind of what we have to deal with. The only way we can combat this is have something consistent and explicit.

> What I wanted do with this library, if I could, is create a new guarantee around style. [In Elm] we have this awesome guarantee, if it compiles: no runtime exceptions. That's so cool. What does that mean for a guarantee with style? If it compiles, our layout is fully explicit.

[Choosing Features - Kevin Lynagh - Deconstruct 2017](https://www.deconstructconf.com/2017/kevin-lynagh-choosing-features)

> And the final thing that we did to communicate this model, it might seem a little strange, but we actually spent a lot of time introducing errors into the system. I guess the best way to motivate why errors are helpful is to imagine situations where you don't have errors, which brings me back to CSS. In CSS, you can use positioning to say, I want this 20 pixel wide thing to be 10 pixels from the left. Or you can say I want it to be 10 pixels from the right. And if you resize this thing, it's going to stay pinned 10 pixels there. And you can even say I want it to be 10 pixels from the left, and 10 pixels from the right, and if you resize it, it's going to adjust the width to match.

> So the question I have is, what happens when you specify all three? And if you like gambling, this is a great time to turn to your neighbor and ask what they think, and place a bet. What you think is going to happen when you specify all three of these things. Because to be clear, if this parent box is 100 pixels wide, you're saying I want a 20 pixel thing to be 10 pixels from the left and 10 pixels from the right. This is impossible, like mathematically. You cannot do this. But interestingly, CSS will not raise an error. It will do something. In some ways, it makes sense for CSS, because browsers have to parse all this garbage on the internet, with broken tags and things that just aren't-- like impossible, it still wants to draw something for you. But if you're trying to build something, if you're trying to internalize how this model works, not having errors is actually very harmful, because you might think that this is a reasonable thing to ask, and you will get away with thinking that, because it'll still draw you a box somewhere. And this is a homework exercise, I don't know what happens here.

> In our tool, we have the same problem. So you could specify pixels all along an axis and ask for something impossible, but instead of just doing something, and dropping one of those implicitly, we decided we should just raise an error. So we actually turn whatever you're working on into this little red box with an exclamation point, and if you zoom in here, we give you the error right in the control. And it says hey, something needs to be stretchy here, because this is not going to work. And if that doesn't make sense to you still, you can click on it, and it explains a little more, what's going on. And you can say like, look, you can make the top part stretchy or the bottom part, or the height can be stretchy, but something has to be stretchy here for this to work.

> And this, again, it really helps you if you're learning, you're coming into the system-- there's a lot of error-- error messages have such a bad rap, because they're so unhelpful usually. It's like, something went wrong, you were wrong, and then you have one button that's like, OK. So But they don't have to be that way. I wanted to give a shout out about Elm's errors, I was going to talk about that, but I haven't already did all that. It's awesome though, because this is not rocket science to make errors like this. If you're making a compiler, or some other tool, you just have to think about how things might go wrong, and then spend a couple of minutes being an empathetic human being, and just saying, how can we help this person use this thing better?

## Prior art

- https://github.com/frenic/csstype
- https://github.com/mdgriffith/style-elements
- https://subformapp.com
- https://github.com/SentiaAnalytics/bs-css
- https://github.com/threepointone/bs-nice
- https://github.com/rtsao/styletron/issues/68#issuecomment-271801234
  - https://github.com/rtsao/sson
  - https://github.com/rtsao/lostyle
- https://gist.github.com/sarahlim/c44df66647fe9a252b0064d3259fde74
- https://github.com/captainbrosset/useless-css-properties
