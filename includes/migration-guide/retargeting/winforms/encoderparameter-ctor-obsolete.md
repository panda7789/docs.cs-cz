---
ms.openlocfilehash: b4e062fe3a00b76da144e706841f87b2a95888e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088485"
---
### <a name="encoderparameter-ctor-is-obsolete"></a>EncoderParameter ctor je zastaralý.

|   |   |
|---|---|
|Podrobnosti|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)> Konstruktor je nyní zastaralé a budou zavedeny upozornění sestavení, pokud se používá.|
|Doporučení|I když <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)>konstruktoru bude pokračovat v práci, následující konstruktor by měl místo toho použít při opětovné kompilaci kódu pomocí nástroje rozhraní .NET Framework 4.5, aby upozornění zastaralé sestavení: <xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Drawing.Imaging.EncoderParameterValueType,System.IntPtr)>.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Drawing.Imaging.EncoderParameter.%23ctor(System.Drawing.Imaging.Encoder,System.Int32,System.Int32,System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
