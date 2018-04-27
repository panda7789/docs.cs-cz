---
title: Statická třída návrhu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a6143b128442db1ac090f0b3680f94b1ac9a9cfc
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="static-class-design"></a>Statická třída návrhu
Statická třída je definovaný jako třída, která obsahuje jenom statické členy (samozřejmě kromě členů instance zděděno z <xref:System.Object?displayProperty=nameWithType> a které by mohly mít soukromý konstruktor). Některé jazyky poskytují integrovanou podporu pro statické třídy. V C# 2.0 nebo novější Pokud třída je deklarován jako statický, zapečetěné, je abstraktní a žádní členové instance můžete přepsat nebo deklarován.  
  
 Statické třídy jsou kompromis mezi čistý objektově orientované návrhu a jednoduchost. Běžně se používají k poskytování zástupce dalších operací (například <xref:System.IO.File?displayProperty=nameWithType>), držitele rozšiřující metody nebo funkce, pro které je úplné objektově orientované obálku bude vyplacena neoprávněně (například <xref:System.Environment?displayProperty=nameWithType>).  
  
 **PROVEĎTE ✓** statické třídy používejte opatrně.  
  
 Statické třídy má být použit pouze jako podpora třídy pro základní objektově orientované rozhraní Framework.  
  
 **X nesmí** statické třídy považovat za různé sady.  
  
 **X nesmí** deklarovat nebo přepsání instance členové statické třídy.  
  
 **PROVEĎTE ✓** deklarovat statické třídy jako zapečetěné, abstraktní a přidejte konstruktor privátní instance, pokud si programovací jazyk nemá integrovanou podporu pro statické třídy.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu typu](../../../docs/standard/design-guidelines/type.md)  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
