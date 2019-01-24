---
title: Návrh rozhraní
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: KrzysztofCwalina
ms.openlocfilehash: 1f982aa37f92b7270725574d949989ca120297d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660144"
---
# <a name="interface-design"></a>Návrh rozhraní
I když většina rozhraní API jsou nejlepším modelovány pomocí třídy a struktury, existují případy, ve kterých jsou vhodnější rozhraní, nebo je jedinou možností.  
  
 Modul CLR nepodporuje vícenásobnou dědičnost (například tříd CLR nemůže dědit z více než jedné základní třídy), ale umožní typy implementovat jedno nebo více rozhraní kromě dědí ze základní třídy. Rozhraní se proto často používají k dosažení efekt vícenásobná dědičnost. Například <xref:System.IDisposable> je rozhraní, která umožňuje typy pro podporu disposability nezávisle na jiných hierarchii dědičnosti, ve kterém se mají zapojit.  
  
 Další situace, při definování, které je vhodné rozhraní je při vytváření jednotné rozhraní, které může podporovat několik typů, včetně některých typů hodnot. Typy hodnot nemůže dědit z typů jiných než <xref:System.ValueType>, ale mohou implementovat rozhraní, pomocí rozhraní je jedinou možností negace běžné základního typu.  
  
 **✓ DO** definovat rozhraní, pokud potřebujete některé společné rozhraní API jsou podporováni sada typy, které obsahuje typy hodnot.  
  
 **✓ CONSIDER** definování rozhraní, pokud potřebujete podporu pro typy, které již dědí od jiný typ jeho funkcí.  
  
 **X AVOID** pomocí rozhraní značky (rozhraní s žádní členové).  
  
 Pokud budete muset označit třídu jako mají konkrétní charakteristiku (značky), obecně platí, použijte vlastní atribut, nikoli rozhraní.  
  
 **✓ DO** zadejte alespoň jeden typ, který je implementací rozhraní.  
  
 Provádí se to pomáhá k ověření návrhu rozhraní. Například <xref:System.Collections.Generic.List%601> je implementace <xref:System.Collections.Generic.IList%601> rozhraní.  
  
 **✓ DO** zadejte alespoň jeden rozhraní API, které zabírá jednotlivá rozhraní definujete (metoda, která bere rozhraní jako parametr nebo vlastnost zadán jako rozhraní).  
  
 Provádí se to pomáhá k ověření návrhu rozhraní. Například <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> využívá <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> rozhraní.  
  
 **X DO NOT** přidat členy do rozhraní, které se dříve dodaný.  
  
 Mohlo by narušil implementace rozhraní. Pokud se chcete vyhnout problémy se správou verzí byste měli vytvořit nové rozhraní.  
  
 S výjimkou případů popsaných v těchto pokynů by měly obecně platí, zvolte třídy, nikoli rozhraní při navrhování opakovaně použitelné knihovny spravovaného kódu.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)
- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
