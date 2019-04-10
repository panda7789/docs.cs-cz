---
ms.openlocfilehash: a6f93bbdf39a1b525e2daeb12afc3a6392a66e30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235384"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>Deserializace MailMessage objekty serializované v rozhraní .NET Framework 4.5 může selhat.

|   |   |
|---|---|
|Podrobnosti|Od verze rozhraní .NET Framework 4.5, <xref:System.Web.Mail.MailMessage> objekty může obsahovat jiné znaky než ASCII. V rozhraní .NET Framework 4 jsou podporovány pouze znaky ASCII. <xref:System.Web.Mail.MailMessage> objekty, které obsahují ne ASCII znaky a, které jsou serializovány v rozhraní .NET Framework 4.5 nebo novější, nemohou být deserializovány v rozhraní .NET Framework 4.|
|Doporučení|Ujistěte se, že váš kód obsahuje zpracování výjimek při deserializaci <xref:System.Web.Mail.MailMessage> objektu.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
