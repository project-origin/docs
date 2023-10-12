# Issue transaction

> [!NOTE]
> The issue command is only valid for **Issuing bodies** for a given area.

It enables the issuing body to issue a new Granular Certificate.

When issued, **1** initial slice is created. The **quantity** and **publickey** parameters are used to create the initial slice.

## Data in the transaction

The following data is required to issue a new Granular Certificate:

| Parameter | Description |
| :--- | :--- |
| **certificate_id** | The [Federated Certificate ID](../federated-certifate-id.md) of the certificate to issue. |
| **type** | The type which can be either production or consumption. |
| **period** | The [period](../attributes.md#period) where the certificate relates to. |
| **grid_area** | The [grid area](../attributes.md#grid-area) where the certificate relates to. |
| **quantity_commitment** | Which holds the quantity of the certificate in a [Pedersen commitment](../../pedersen-commitments.md). |
| **owner_public_key** | The public key of the owner of the certificate. |
| **attributes** | Additional [secondary attributes](../attributes.md#secondary-attributes) of the certificate. |
