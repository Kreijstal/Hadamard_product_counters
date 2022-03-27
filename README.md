# Hadamard_product_counters

Functions to compute the Hadamard product, its residual, and its dual residual on counters. The code is written on top of the library [ETVO](http://perso-laris.univ-angers.fr/~cottenceau/etvo.html) ((Event|Time)-Variant Operators).

See <http://perso-laris.univ-angers.fr/~cottenceau/etvo.html> for the start-up instructions.
The added functions are `hadamard_prod`, `hadamard_res`, and `hadamard_dualres`, which compute the Hadamard product, its residual, and its dual residual, respectively.
They accept two inputs, which must be elements of class `gd` (monomials), `poly` (polynomials), or `series` (ultimately periodic series).

## Code example

Consider monomials ![equation](https://latex.codecogs.com/png.image?%5Cbg_white%20r_1&space;=&space;5\delta^2) and ![equation](https://latex.codecogs.com/png.image?%5Cbg_white%20r_2&space;=&space;3\delta^2).
The following code produces ![equation](https://latex.codecogs.com/png.image?%5Cbg_white%20r_1\odot&space;r_2&space;=&space;8\delta^2), ![equation](https://latex.codecogs.com/png.image?%5Cbg_white%20r_1\odot^\sharp&space;r_2&space;=&space;2\delta^{&plus;\infty}), and ![equation](https://latex.codecogs.com/png.image?%5Cbg_white%20r_1\odot^\flat&space;r_2&space;=&space;2\delta^2).

```cpp
void main()
{
    // initialize monomials
    gd r_1, r_2, res_odot, res_odot_sharp, res_odot_flat;

    // define $r_1$ and $r_2$
    r_1 = gd(5, 2); 
    r_2 = gd(3, 2);

    // print $r_1$ and $r_2$
    cout << "r_1 = " << r_1 << endl;
    cout << "r_2 = " << r_2 << endl;

    // compute $r_1\odot r_2$, $r_1\odot^\sharp r_2$, and $r_1\odot^\flat r_2$
    res_odot = hadamard_prod(r_1, r_2);
    res_odot_sharp = hadamard_res(r_1, r_2);
    res_odot_flat = hadamard_dualres(r_1, r_2);

    // print the results
    cout << "res_odot = " << res_odot << endl;
    cout << "res_odot_sharp = " << res_odot_sharp << endl;
    cout << "res_odot_flat = " << res_odot_flat << endl;
}
```

Other examples are documented in the technical report *The Hadamard product, its residual, and its dual residual in the dioid of counters: algorithms and implementation in C++*, available on [arxiv](https://arxiv.org/).
