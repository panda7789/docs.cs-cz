---
title: Rozhraní návrhu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8636653ca856693961cbfc73e9170410ed2cd361
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="interface-design"></a>Rozhraní návrhu
I když většina rozhraní API jsou nejlépe modelovány pomocí třídy a struktury, existují případy, ve kterých jsou vhodnější rozhraní, nebo je jedinou možností.  
  
 Modul CLR nepodporuje vícenásobná dědičnost (tj, tříd CLR nemůže Zdědit z více než jeden základní třídy), ale neumožňuje typy implementovat jednu nebo více rozhraní kromě dědění ze základní třídy. Rozhraní se proto často používají k dosažení účinku vícenásobná dědičnost. Například <xref:System.IDisposable> je rozhraní, které umožňuje typy pro podporu disposability nezávislé na dalších hierarchie dědičnosti, ve které se chcete zúčastnit.  
  
 Další situace při definování, které je vhodné rozhraní je při vytváření jednotné rozhraní, které může podporovat několik typů, včetně některých typů hodnot. Typy hodnot nemůže Zdědit z typy jiné než <xref:System.ValueType>, ale implementovaly rozhraní, tak přes rozhraní je jedinou možností Chcete-li poskytovat běžné základního typu.  
  
 **PROVEĎTE ✓** definovat rozhraní, pokud potřebujete některé společné rozhraní API jsou podporováni sada typy, které obsahuje typy hodnot.  
  
 **✓ ZVAŽTE** definování rozhraní, pokud potřebujete podporu pro typy, které již dědí od jiný typ jeho funkcí.  
  
 **X nepoužívejte** pomocí rozhraní značky (rozhraní s žádní členové).  
  
 Pokud potřebujete označte třídu tak, že má zvláštní vlastností (značka), obecně platí, použijte vlastní atribut, nikoli rozhraní.  
  
 **PROVEĎTE ✓** zadejte alespoň jeden typ, který je implementací rozhraní.  
  
 Díky této pomáhá ověření návrhu rozhraní. Například <xref:System.Collections.Generic.List%601> je implementací <xref:System.Collections.Generic.IList%601> rozhraní.  
  
 **PROVEĎTE ✓** zadejte alespoň jeden rozhraní API, které zabírá jednotlivá rozhraní definujete (metoda, která bere rozhraní jako parametr nebo vlastnost zadán jako rozhraní).  
  
 Díky této pomáhá ověření návrhu rozhraní. Například <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> spotřebovává <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> rozhraní.  
  
 **X nesmí** přidat členy do rozhraní, které se dříve dodaný.  
  
 Tím by došlo k přerušení implementace rozhraní. Aby se zabránilo problémům s verzemi, byste měli vytvořit nové rozhraní.  
  
 S výjimkou případů popsaných v těchto pokynů měli byste, obecně vybrat třídy, nikoli rozhraní návrhu opakovaně použitelné knihovny spravovaného kódu.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
