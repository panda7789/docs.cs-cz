---
ms.openlocfilehash: e2bca42daebd25667ab2f312d5e59089b986503c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234636"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>Při použití AntiXSSEncoderu se měnily mezery ve víceřádkových textových polích ASP.Net

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.0 se při používání nástroje <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=name> během zpětného vystavení mezi řádky víceřádkového textového pole vkládaly řádky navíc. V rozhraní .NET Framework 4.5 tato nadbytečná zalomení řádku nejsou, ale pouze v případě, že i webová aplikace cílí na verzi .NET Framework 4.5.|
|Doporučení|Mějte na paměti, že u webových aplikací z verze 4.0, u nichž bylo změněno cílení na verzi .NET Framework 4.5, se můžou víceřádková textová pole vylepšit tím, že už se do nich nevkládají nadbytečná zalomení řádku. Pokud to není žádoucí, můžete v aplikaci dosáhnout starého chování tak, že ji spustíte v rozhraní .NET Framework 4.5 a budete cílit na verzi .NET Framework 4.0.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Změna cílení|
