---
ms.openlocfilehash: 150b98255b3075a8fe8cad60ce234206b788a5f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617184"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>Při použití AntiXSSEncoderu se měnily mezery ve víceřádkových textových polích ASP.Net

#### <a name="details"></a>Podrobnosti

V rozhraní .NET Framework 4.0 se při používání nástroje <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName> během zpětného vystavení mezi řádky víceřádkového textového pole vkládaly řádky navíc. V rozhraní .NET Framework 4.5 tato nadbytečná zalomení řádku nejsou, ale pouze v případě, že i webová aplikace cílí na verzi .NET Framework 4.5.

#### <a name="suggestion"></a>Návrh

Mějte na paměti, že u webových aplikací z verze 4.0, u nichž bylo změněno cílení na verzi .NET Framework 4.5, se můžou víceřádková textová pole vylepšit tím, že už se do nich nevkládají nadbytečná zalomení řádku. Pokud to není žádoucí, můžete v aplikaci dosáhnout starého chování tak, že ji spustíte v rozhraní .NET Framework 4.5 a budete cílit na verzi .NET Framework 4.0.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.5         |
| Typ    | Změna cílení |
