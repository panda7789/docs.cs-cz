---
title: Volba mezi třídou a strukturou
ms.date: 10/22/2008
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
ms.openlocfilehash: 34ab2589364e244fed1c64c1703205fb4b0832e8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709514"
---
# <a name="choosing-between-class-and-struct"></a>Volba mezi třídou a strukturou
Jedno ze základních rozhodnutí o návrhu každé plošky návrháře architektury je bez ohledu na to, zda je možné navrhnout typ jako třídu (odkazový typ) nebo jako strukturu (typ hodnoty). Dobrým porozumění rozdílům v chování typů odkazu a hodnot je rozhodující při této volbě.  
  
 První rozdíl mezi typy odkazů a typy hodnot, které budeme brát v úvahu, je, že typy odkazů jsou přiděleny na haldě a uvolňování paměti, zatímco typy hodnot jsou přiděleny buď v zásobníku, nebo vloženy v případě, že je zásobník unwind nebo při zrušení přidělení jejich nadřazeného typu. Proto jsou alokace a navracení hodnotových typů všeobecně levnější než přidělení a zrušení přidělení typů odkazů.  
  
 Dále jsou pole typů odkazů rozdělena mimo řádek, což znamená, že prvky pole jsou pouze odkazy na instance typu odkazu, který je umístěn na haldě. Pole hodnot typu jsou přidělena jako vložená, což znamená, že prvky pole jsou skutečnými instancemi typu hodnoty. Proto jsou přidělení a dealokace polí hodnotových typů mnohem levnější než přidělení a zrušení přidělení polí typu odkazu. Kromě toho ve většině případů typ hodnoty pole představuje mnohem lepší rozsah odkazů.  
  
 Další rozdíl se týká využití paměti. Typy hodnot se při přetypování na typ odkazu nebo na jedno z rozhraní, které implementují, vrátí do pole. Po přetypování zpátky na typ hodnoty se rozstanou. Vzhledem k tomu, že pole jsou objekty, které jsou přiděleny haldě a jsou uvolněny do paměti, příliš mnoho zabalení a rozbalení může mít negativní vliv na haldu, uvolňování paměti a nakonec výkon aplikace.  Naopak žádné takové zabalení nevzniká jako přetypování typů odkazů. (Další informace naleznete v tématu [zabalení a rozbalení](../../csharp/programming-guide/types/boxing-and-unboxing.md)).
  
 V dalším kroku přiřazení typu odkazu kopírují odkaz, zatímco přiřazení typu hodnoty kopírují celou hodnotu. Proto přiřazení velkých typů odkazů jsou levnější než přiřazení typů velkých hodnot.  
  
 Nakonec odkazové typy jsou předány odkazem, zatímco typy hodnot jsou předány hodnotou. Změny instance typu odkazu ovlivňují všechny odkazy odkazující na instanci. Instance typu hodnoty jsou zkopírovány, když jsou předány hodnotou. Když dojde ke změně instance hodnotového typu, samozřejmě nemá vliv na žádnou z jeho kopií. Vzhledem k tomu, že kopie nejsou vytvořeny explicitně uživatelem, ale jsou implicitně vytvořeny, když jsou předány argumenty nebo vrátí návratové hodnoty, mohou být typy hodnot, které lze změnit, matoucí pro mnoho uživatelů. Proto by měly být typy hodnot neměnné.  
  
 Jako pravidlo pro palec by většina typů v rozhraní měla být třídy. Existují však některé situace, ve kterých charakteristiky typu hodnoty usnadňují používání struktur.  
  
 **✓ CONSIDER** definice struktury místo třídu, pokud instance typu jsou malé a běžně krátkodobou nebo jsou běžně součástí jiné objekty.  
  
 **X AVOID** definice struktury, pokud má tento typ všechny následující vlastnosti:  
  
- Logicky představuje jedinou hodnotu, podobně jako primitivní typy (`int`, `double`atd.).  
  
- Má velikost instance 16 bajtů.  
  
- Je neměnný.  
  
- Nemusí být často ohraničená.  
  
 Ve všech ostatních případech byste měli definovat typy jako třídy.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
