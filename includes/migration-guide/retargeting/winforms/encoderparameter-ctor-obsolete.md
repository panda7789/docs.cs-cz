---
ms.openlocfilehash: 4ad7c4c2781480c08ad4cf27e40de445b1c50671
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617246"
---
### <a name="encoderparameter-ctor-is-obsolete"></a>EncoderParameter ctor je zastaralý.

#### <a name="details"></a>Podrobnosti

<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>Konstruktor je zastaralý nyní a při použití zavede upozornění sestavení.

#### <a name="suggestion"></a>Návrh

I když <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> konstruktor bude i nadále fungovat, měli byste použít následující konstruktor, abyste zabránili zastaralému upozornění sestavení při opětovném kompilování kódu pomocí nástrojů .NET Framework 4,5: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)> .

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.5         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>
