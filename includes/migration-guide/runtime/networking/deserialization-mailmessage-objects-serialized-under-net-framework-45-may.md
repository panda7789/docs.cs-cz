---
ms.openlocfilehash: ad953a1562db407c04d7860c60eb5964fe6fe2ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620038"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>Deserializace objektů MailMessage serializovaných v .NET Framework 4,5 může selhat.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,5 <xref:System.Web.Mail.MailMessage> mohou objekty obsahovat jiné znaky než ASCII. V .NET Framework 4 jsou podporovány pouze znaky ASCII. <xref:System.Web.Mail.MailMessage>objekty, které obsahují znaky jiné než ASCII a které jsou serializovány pod .NET Framework 4,5 nebo novější, nelze deserializovat v .NET Framework 4.

#### <a name="suggestion"></a>Návrh

Ujistěte se, že váš kód poskytuje zpracování výjimek při deserializaci <xref:System.Web.Mail.MailMessage> objektu.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
