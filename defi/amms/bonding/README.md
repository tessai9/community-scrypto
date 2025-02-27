# scrypto-bonding

scrypto-bonding: A Scrypto package for creating and using bonding curves as an automated market maker on Radix

The main blueprint to interact with is `BondingAMM`.  It has buy/sell functionality against a single
bonding curve defined by a plugable second component.  It will instantiate a component from the `RatioBondingCurve`
blueprint if no other curve component is provided.

There is also an extrememly simple `BasicBondingCurve` blueprint (more like a flat line) which could be used to implement
a simple "wrapped" or "virtual" token from another.  Or it's a a good template for making your own curve component.

Some useful utilities are included too.  An internal crate is used to provide the `blueprint_stub` macro which
automates creating stub functions from a trait so calling another component is ergonomic.  Also included and
used for the `RatioBondingCurve` is a reusable arbitrary precision number implmentation that converts to/from Decimal
It is precise but not yet optimized.  Bounded (BigInt) or unbounded (BigRational) precision is configurable with a feature flag.

## Bonuses:

* This package is well tested (though not completely) with both unit and integration tests.  Integration
testing is not as easy as it should be, but using the [`scrypto-unit`] library helps a whole lot

* Key portions of `BondingAMM` are implemented using [`scrypto_statictypes`] which provides compile-time resource
checking and additional runtime checking for enhanced producitivity and safety.

[`scrypto-unit`]: https://github.com/plymth/scrypto-unit
[`scrypto_statictypes`]: https://github.com/devmannic/scrypto_statictypes

## References:

If you want to read more about bonding curves here some things that might be useful:

Reading List
* https://blog.relevant.community/bonding-curves-in-depth-intuition-parametrization-d3905a681e0a?gi=8df5128ab916
* https://blog.relevant.community/how-to-make-bonding-curves-for-continuous-token-models-3784653f8b17
* https://billyrennekamp.medium.com/converting-between-bancor-and-bonding-curve-price-formulas-9c11309062f5
* https://yos.io/2017/11/10/bonding-curves/
* https://medium.com/linum-labs/intro-to-bonding-curves-and-shapes-bf326bc4e11a
* https://discourse.sourcecred.io/t/bonding-curve-references/271

Code
* https://github.com/oed/bonding-curves/blob/master/contracts/PolynomialCurvedToken.sol
* https://github.com/OpenZeppelin/openzeppelin-contracts/blob/7b7ff729b82ea73ea168e495d9c94cb901ae95ce/contracts/math/Power.sol
* https://github.com/bancorprotocol/contracts-solidity/blob/c9adc95e82fdfb3a0ada102514beb8ae00147f5d/solidity/contracts/converter/BancorFormula.sol


License: MIT OR Apache-2.0
