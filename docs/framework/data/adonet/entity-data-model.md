---
title: Entity Data Model
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1a1bdeffcc85383d241c277240187ede41401cd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="entity-data-model"></a>Entity Data Model
Entity Data Model (EDM) je sada koncepty, které popisují strukturu dat, bez ohledu na jeho uložené formuláře. Vychází z modelu vztah entit popsaného Petr Svoboda v 1976 jazyků EDM, ale také založený na modelu vztah entit a rozšiřuje jeho tradiční používá.  
  
 EDM řeší problémy, které způsobit s daty uloženými v celou řadu forem. Představte si třeba firmy, která ukládá data v relačních databází, textové soubory, soubory XML, tabulky a sestavy. To představuje významné problémy v datech modelování, návrh aplikace a přístup k datům. Při navrhování aplikace data, na výzvu je napsat kód efektivní a udržovatelný bez omezení přístupu k datům efektivní, úložiště a škálovatelnost. Pokud data má relační strukturu, jsou velmi efektivní přístup k datům, úložiště a škálovatelnost, ale zápis efektivní a udržovatelného kódu je podstatně obtížnější. Pokud data strukturu objekt, jsou kompromisy vrátit: psaní kódu efektivní a udržovatelný dodává za cenu přístup k datům efektivní, úložiště a škálovatelnost. I když můžete najít rovnováhu mezi tyto kompromisy, vyvolány další výzvy při přesunutí dat z jednoho formátu do jiného. Datový Model Entity řeší tyto problémy prostřednictvím popisu strukturu dat z hlediska entity a vztahy, které jsou nezávislé na žádné schéma úložiště. Díky tomu uložené formu dat. důležité aplikace návrh a vývoj. A protože entity a vztahy popisují strukturu dat, protože se používá v aplikaci (ne jeho uložené formulář), můžete rozvíjet jako zpracovaní aplikace.  
  
 A `conceptual model` je konkrétní reprezentace strukturu dat jako entity a vztahy a je obvykle definováno v jazyce specifické pro doménu (DSL), který implementuje koncepty EDM. [Koncepční schéma definition language (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) je příkladem jazyk specifické pro doménu. Entity a vztahy, které jsou popsané v konceptuálním modelu lze považovat za abstrakce objektů a přidružení v aplikaci. To umožňuje vývojářům soustředit na konceptuální model bez obav o schéma úložiště a umožňuje je napsat kód s efektivitu a jeho udržovatelnost v paměti. Mezitím Designer schéma úložiště můžete soustředit na efektivitu přístup k datům, úložiště a škálovatelnost.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Témata v této části popisují koncepty datového modelu Entity. Všechny DSL, který implementuje EDM by měla obsahovat konceptů popsaných v tomto poli. Všimněte si, že [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) CSDL používá k definování konceptuálních modelech. Další informace najdete v tématu [CSDL specifikace](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).  
  
 [Koncepty modelu EDM (Entity Data Model)](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [Model EDM (Entity Data Model): Obory názvů](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [Model EDM (Entity Data Model): Primitivní datové typy](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [Model EDM (Entity Data Model): Dědičnost](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [association end](../../../../docs/framework/data/adonet/association-end.md)  
  
 [association end multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [association set](../../../../docs/framework/data/adonet/association-set.md)  
  
 [association set end](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [association type](../../../../docs/framework/data/adonet/association-type.md)  
  
 [complex type](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [entity container](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [entity key](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [entity set](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [entity type](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [facet](../../../../docs/framework/data/adonet/facet.md)  
  
 [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [model-declared function](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [model-defined function](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [navigation property](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [property](../../../../docs/framework/data/adonet/property.md)  
  
 [referential integrity constraint](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a>Viz také  
 [Nástroje modelu ADO.NET Entity Data Model](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)  
 [Přehled souboru EDMX](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Specifikace CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
