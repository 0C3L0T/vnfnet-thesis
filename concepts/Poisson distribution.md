
A Poisson distribution is a probability distribution that describes the number of events occurring in a fixed interval of time or space when the events happen with a known constant rate and are independent of the time since the last event. It's often used in situations where events occur randomly and independently, such as the number of phone calls received by a call center in a given hour, the number of accidents at a particular intersection in a day, or the number of emails arriving in an inbox per hour.

The Poisson distribution is characterized by a single parameter, usually denoted by λ (lambda), which represents the average rate of occurrence of the events in the given interval. The probability mass function of a Poisson distribution is given by:

$$ P(X=k) = \frac{{e^{-\lambda} \lambda^k}}{{k!}} $$

Where:
- \( P(X=k) \) is the probability of observing \( k \) events,
- \( e \) is the base of the natural logarithm (approximately 2.71828),
- \( \lambda \) is the average rate of occurrence of the events,
- \( k \) is the number of events,
- \( k! \) denotes the factorial of \( k \), and
- ($e^{-\lambda}$) is the term used to normalize the distribution so that the sum of probabilities equals 1.

The Poisson distribution is often used as an approximation to the binomial distribution when the number of trials is large and the probability of success is small, with \( \lambda = np \), where \( n \) is the number of trials and \( p \) is the probability of success.