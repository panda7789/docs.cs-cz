---
ms.openlocfilehash: 38c35f3f6f2262d06409690d2326d9b982e1ec86
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235396"
---
### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>Hostitelské ovládací prvky spravovaného prohlížeče v rozhraní .NET Framework 1.1 a 2.0 jsou zablokované.

|   |   |
|---|---|
|Podrobnosti|Hostování těchto ovládacích prvků je blokováno v aplikaci Internet Explorer.|
|Doporučení|Internet Explorer nespustí aplikaci, která používá hostovací ovládací prvky spravovaného prohlížeče. Předchozí chování lze obnovit nastavením hodnoty EnableIEHosting podklíče registru <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> k <code>1</code> pro x86 systémy a pro 32bitové procesy v x64 systémů a tím, že nastavíte <code>EnableIEHosting</code> podklíče registru <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code>k <code>1</code> pro 64bitové procesy v x64 systémy.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
