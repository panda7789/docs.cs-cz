---
title: Vnořené typy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
ms.openlocfilehash: dd13116b13ac8e2d7a3af6ef014eb4f393909515
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743699"
---
# <a name="nested-types"></a>Vnořené typy
Vnořený typ je typ definovaný v oboru jiného typu, který se nazývá nadřazený typ. Vnořený typ má přístup ke všem členům svého nadřazeného typu. Má například přístup k soukromým polím definovaným v nadřazeném typu a chráněným polím definovaným ve všech nadřazených členů nadřazených typů.

 Obecně platí, že vnořené typy by se měly používat zřídka. Z tohoto důvodu je k dispozici několik důvodů. Někteří vývojáři nejsou plně obeznámeni s konceptem. Tito vývojáři mohou mít například problémy s syntaxí deklarování proměnných vnořených typů. Vnořené typy jsou také velmi úzce spojeny s jejich nadřazenými typy a jako takové nejsou vhodné pro obecné typy.

 Vnořené typy jsou nejvhodnější pro podrobnosti o implementaci modelování jejich nadřazených typů. Koncový uživatel by měl definovat proměnné vnořeného typu zřídka a téměř nikdy by neměl muset explicitně vytvářet instance vnořených typů. Například enumerátor kolekce může být vnořeným typem kolekce. Enumerátory jsou obvykle vytvořeny pomocí jejich ohraničujícího typu a protože mnoho jazyků podporuje příkaz foreach, proměnné čítače výčtu zřídka musí být deklarovány koncovým uživatelem.

 ✔️ použít vnořené typy, pokud je relace mezi vnořeným typem a jeho vnějším typem taková, že je žádoucí sémantika přístupnost členů.

 ❌ nepoužívejte veřejné vnořené typy jako konstrukci logického seskupení; Použijte obory názvů pro tento.

 ❌ Vyhněte se veřejně vystaveným vnořeným typům. Jedinou výjimkou je, že proměnné vnořeného typu musí být deklarovány pouze ve výjimečných scénářích, jako je například použití podtříd nebo jiné pokročilé scénáře přizpůsobení.

 ❌ nepoužívají vnořené typy, pokud je pravděpodobně odkazován na typ mimo nadřazený typ.

 Například výčet předaný metodě definovanému pro třídu by neměl být definován jako vnořený typ ve třídě.

 ❌ nepoužívají vnořené typy, pokud musí být vytvořeny instance klientského kódu.  Má-li typ veřejný konstruktor, neměl by být pravděpodobně vnořený.

 Pokud lze vytvořit instanci typu, která označuje, že typ má místo v rozhraní vlastní (můžete ho vytvořit, pracovat s ním a zničit jej bez použití vnějšího typu), a proto by neměl být vnořen. Vnitřní typy by se neměly široce používat vně vnějšího typu bez jakéhokoli vztahu k vnějšímu typu.

 ❌ nedefinovat vnořený typ jako člen rozhraní. Mnohé jazyky tuto konstrukci nepodporují.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
