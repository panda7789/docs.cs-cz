---
title: Pokyny k návrhu typu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 3e2fe7168bd0029d8f0e8f69a136c9089032973f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709020"
---
# <a name="type-design-guidelines"></a>Pokyny k návrhu typu
Z perspektivy CLR existují pouze dvě kategorie typů – typy odkazů a typy hodnot – ale pro účely diskuze o návrhu rozhraní rozdělíme typy do více logických skupin, z nichž každá má konkrétní pravidla návrhu.  
  
 Třídy jsou obecné velikosti typů odkazů. Tvoří velkou část typů ve většině platforem. Třídy odtřídí své oblíbenosti na bohatou sadu objektově orientovaných funkcí, které podporují, a jejich obecné použitelnosti. Základní třídy a abstraktní třídy jsou speciální logické skupiny, které souvisejí s rozšiřitelnou.  
  
 Rozhraní jsou typy, které mohou být implementovány oběma typy odkazu a typy hodnot. Mohou proto sloužit jako kořeny polymorfních hierarchií typů odkazů a typů hodnot. Kromě toho lze rozhraní použít k simulaci vícenásobné dědičnosti, která není nativně podporována modulem CLR.  
  
 Struktury jsou obecné typy hodnot a měly by být rezervovány pro malé, jednoduché typy, podobně jako jazykové primitivy.  
  
 Výčty jsou zvláštní případ hodnotových typů, které slouží k definování krátkých sad hodnot, například dnů v týdnu, barev konzoly atd.  
  
 Statické třídy jsou typy, které mají být kontejnery pro statické členy. Obvykle se používají k poskytnutí zástupců pro jiné operace.  
  
 Delegáti, výjimky, atributy, pole a kolekce jsou všechny zvláštní případy odkazových typů určených pro konkrétní použití a pokyny pro jejich návrh a použití jsou popsány jinde v této knize.  
  
 **✓ DO** zajistěte, aby byl každý typ dobře definované sadě souvisejících členů, nejen náhodné kolekce funkcí, které nejsou.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Volba mezi třídou a strukturou](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [Návrh abstraktní třídy](../../../docs/standard/design-guidelines/abstract-class.md)  
 [Návrh statické třídy](../../../docs/standard/design-guidelines/static-class.md)  
 [Návrh rozhraní](../../../docs/standard/design-guidelines/interface.md)  
 [Návrh struktury](../../../docs/standard/design-guidelines/struct.md)  
 [Návrh výčtu](../../../docs/standard/design-guidelines/enum.md)  
 [Vnořené typy](../../../docs/standard/design-guidelines/nested-types.md)  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
