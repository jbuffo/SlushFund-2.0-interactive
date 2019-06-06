# SlushFund-2.0-interactive
One-Dimensional Reactive Transport Model for Sea Ice

This model simulates the multiphase evolution of ice-ocean interfaces to produce
profiles of ice composition, thermal structure, porosity, and can easily be adapted to
calculate additional quantities (e.g. freezing front velocity, salt expelled from ice, etc.)

Nearly all work is carried out in the file 'SF1D_interactive_v2.m'
This is the file which should be run in MATLAB and calls on the other '.m' files in this package

--------------------------------------------------------------------
Key parameters that can be modified in 'SF1D_interactive_v2.m' to account for unique ice-ocean environments:


t_i - initial time (typically 0)

t_f - final time (of the simulation)

Ttop - surface temperature

Tbottom - ocean temperature

interface_in - initial ice-ocean interface depth (model can struggle for very small values when Ttop is very low)

Tm - melting temperature of pure ice

k_i - thermal conductivity of ice

k_br - thermal conductivity of brine

k_s - molecular diffusivity of salt

dt - time step discretization

dz - spatial step discretization (1cm resolution works quite well and is small enough to capture the dynamics occuring in the system)

H - domain size

c_br - specific heat of brine (initial ocean)

c_i - specific heat of ice

L - latent heat of fusion

S_bottom - ocean salinity

rho_i - ice density

rho_br - brine density (initial ocean density)

STol - salinity tolerance

PhiTol - porosity tolerance

TTol - temperature tolerance

m - cementation exponent (used in Archie's law to describe ion diffusion in porous media)

g - gravity

mu - ocean viscosity

phi_c - critical porosity (used to set percolation threshold for when brine can no longer be transported through the multiphase layer, key for active tracking of interface as below this threshold cells are removed from the active domain and catalogued)

---------------------------------------------------------------------------
Parameters that you may want to change in other files:

In 'one_D_adv_ARD_interactive_v2.m'

delta_T - this parameter is used to calculate freezing point depression due to salt, different salt solutions will likely need
          their own liquidus equations which depend on their unique ionic composition. The sister code Liquidus 1.0 can 
          calculate quadratic liquidus curves for a number of chemistries supported by FREZCHEM 6.2. Otherwise you will have
          to input your own freezing point depression formula.
          
In 'one_D_advective_flux2.m'

beta - density coefficient for salt (when calculating the local Rayleigh number in the mushy layer the impact of brine
       brine salinity on brine density is needed, this parameter relates the change in salinity (ppt) to the change
       in brine density (kg/m^3) and will likely be different for different solutes)
