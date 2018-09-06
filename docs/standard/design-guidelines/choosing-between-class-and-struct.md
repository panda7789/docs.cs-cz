---
title: Volba mezi třídou a strukturou
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06661cb2c34d1da9085fa2129cb0c3307b99097e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865550"
---
# <a name="choosing-between-class-and-struct"></a>Volba mezi třídou a strukturou
Jeden základní rozhodnutí o návrhu, který čelí každý framework designer je, zda navrhnout typu třídy (odkaz na typ) nebo jako – struktura (typu hodnoty). Je velmi důležité při vytvoření tato volba dostatečné povědomí o rozdíly v chování typy odkazů a typy hodnot.  
  
 První rozdíl mezi typy odkazů a typy hodnot, které posoudíme je, že jsou odkazové typy přiděleného v haldě a prováděno uvolnění paměti, že typy hodnot jsou přiděleny na zásobníku nebo vložené v obsahující typy a uvolněna při zásobníku unwinds nebo při jejich nadřazeným typem uvolnění. Přidělování a navrácení typů hodnot, proto jsou obecně levnější než přidělování a navrácení odkazových typů.  
  
 V dalším kroku pole odkazu na typy jsou přidělené mimo řádek, což znamená pole, které prvky jsou pouze odkazy na instance typu odkazu, které se nacházejí na haldě. Pole typu hodnota přidělují vloženě, což znamená, že prvky pole jsou přímo instance typu hodnoty. Přidělování a navrácení pole typu hodnota jsou tedy mnohem levnější než přidělování a navrácení pole typu odkazu. Kromě toho pole typu hodnota ve většině případů je mnohem lepší místo odkazu.  
  
 Další rozdíl se týká využití paměti. Typy hodnot získat zabalená, pokud přetypovat na typ odkazu nebo jednoho z rozhraní, které implementují. Vývojáři získají nezabalený Pokud přetypovat zpět na typ hodnoty. Protože pole jsou objekty, které jsou přiděleny do haldy a jsou uvolněna, příliš mnoho zabalení a rozbalení může mít negativní dopad na haldě systému uvolňování paměti a nakonec výkon aplikace.  Naproti tomu žádné takové zabalení dochází při typy odkazů jsou přetypovat.  
  
 Přiřazení typu odkazu v dalším kroku zkopírujte odkaz, zatímco přiřazení typu hodnoty zkopírujte celou hodnotu. Proto jsou levnější než přiřazení typů velkých hodnot přiřazení velké referenční typy.  
  
 A konečně typy odkazů jsou předány podle odkazu, zatímco hodnotové typy jsou předávány hodnotou. Na instanci typu odkazu ovlivní všechny odkazy odkazující na instanci. Instance typu hodnoty jsou zkopírovány, když jsou předány podle hodnoty. Při změně instance hodnotového typu samozřejmě neovlivňuje některý z jeho kopie. Protože tyto kopie nejsou explicitně vytvořených uživatelem se implicitně vytvářejí, když jsou předány argumenty nebo návratové hodnoty jsou vráceny, může být matoucí pro mnoho uživatelů typů hodnot, které je možné změnit. Typy hodnot, proto by měl být neměnitelný.  
  
 Jako říci by měla být většina typů v rámci třídy. Existují však některé situace, ve kterých vlastnosti typu hodnoty usnadňují vhodnější použít struktury.  
  
 **✓ CONSIDER** definice struktury místo třídu, pokud instance typu jsou malé a běžně krátkodobou nebo jsou běžně součástí jiné objekty.  
  
 **X AVOID** definice struktury, pokud má tento typ všechny následující vlastnosti:  
  
-   Logicky reprezentuje hodnotu single, podobně jako primitivní typy (`int`, `double`atd.).  
  
-   To má velikost instance mladší 16 bajtů.  
  
-   To se nedá změnit.  
  
-   Nebudete muset použít boxing. často.  
  
 Ve všech ostatních případech byste měli definovat vaše typy jako třídy.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)  
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
