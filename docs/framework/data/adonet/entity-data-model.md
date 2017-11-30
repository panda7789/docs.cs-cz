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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 69b72a824e6f9468c9b3d86073243d506382e766
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="entity-data-model"></a>Entity Data Model
Entity Data Model (EDM) je sada koncepty, které popisují strukturu dat, bez ohledu na jeho uložené formuláře. Vychází z modelu vztah entit popsaného Petr Svoboda v 1976 jazyků EDM, ale také založený na modelu vztah entit a rozšiřuje jeho tradiční používá.  
  
 EDM řeší problémy, které způsobit s daty uloženými v celou řadu forem. Představte si třeba firmy, která ukládá data v relačních databází, textové soubory, soubory XML, tabulky a sestavy. To představuje významné problémy v datech modelování, návrh aplikace a přístup k datům. Při navrhování aplikace data, na výzvu je napsat kód efektivní a udržovatelný bez omezení přístupu k datům efektivní, úložiště a škálovatelnost. Pokud data má relační strukturu, jsou velmi efektivní přístup k datům, úložiště a škálovatelnost, ale zápis efektivní a udržovatelného kódu je podstatně obtížnější. Pokud data strukturu objekt, jsou kompromisy vrátit: psaní kódu efektivní a udržovatelný dodává za cenu přístup k datům efektivní, úložiště a škálovatelnost. I když můžete najít rovnováhu mezi tyto kompromisy, vyvolány další výzvy při přesunutí dat z jednoho formátu do jiného. Datový Model Entity řeší tyto problémy prostřednictvím popisu strukturu dat z hlediska entity a vztahy, které jsou nezávislé na žádné schéma úložiště. Díky tomu uložené formu dat. důležité aplikace návrh a vývoj. A protože entity a vztahy popisují strukturu dat, protože se používá v aplikaci (ne jeho uložené formulář), můžete rozvíjet jako zpracovaní aplikace.  
  
 A `conceptual model` je konkrétní reprezentace strukturu dat jako entity a vztahy a je obvykle definováno v jazyce specifické pro doménu (DSL), který implementuje koncepty EDM. [Koncepční schéma definition language (CSDL)](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md) je příkladem jazyk specifické pro doménu. Entity a vztahy, které jsou popsané v konceptuálním modelu lze považovat za abstrakce objektů a přidružení v aplikaci. To umožňuje vývojářům soustředit na konceptuální model bez obav o schéma úložiště a umožňuje je napsat kód s efektivitu a jeho udržovatelnost v paměti. Mezitím Designer schéma úložiště můžete soustředit na efektivitu přístup k datům, úložiště a škálovatelnost.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 Témata v této části popisují koncepty datového modelu Entity. Všechny DSL, který implementuje EDM by měla obsahovat konceptů popsaných v tomto poli. Všimněte si, že [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) CSDL používá k definování konceptuálních modelech. Další informace najdete v tématu [CSDL specifikace](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).  
  
 [Entity Data Model klíčové koncepty](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
  
 [Model Entity Data Model: obory názvů](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)  
  
 [Datového modelu entity: Primitivní datové typy](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)  
  
 [Model Entity Data Model: dědičnosti](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)  
  
 [end přidružení](../../../../docs/framework/data/adonet/association-end.md)  
  
 [násobnost end přidružení](../../../../docs/framework/data/adonet/association-end-multiplicity.md)  
  
 [Sada přidružení](../../../../docs/framework/data/adonet/association-set.md)  
  
 [konce přidružení sady](../../../../docs/framework/data/adonet/association-set-end.md)  
  
 [Typ přidružení](../../../../docs/framework/data/adonet/association-type.md)  
  
 [komplexní typ](../../../../docs/framework/data/adonet/complex-type.md)  
  
 [kontejneru entit](../../../../docs/framework/data/adonet/entity-container.md)  
  
 [klíč entity](../../../../docs/framework/data/adonet/entity-key.md)  
  
 [sada entit](../../../../docs/framework/data/adonet/entity-set.md)  
  
 [Typ entity](../../../../docs/framework/data/adonet/entity-type.md)  
  
 [omezující vlastnost](../../../../docs/framework/data/adonet/facet.md)  
  
 [vlastností cizího klíče](../../../../docs/framework/data/adonet/foreign-key-property.md)  
  
 [deklarovaný modelu – funkce](../../../../docs/framework/data/adonet/model-declared-function.md)  
  
 [model definované funkce](../../../../docs/framework/data/adonet/model-defined-function.md)  
  
 [navigační vlastnost](../../../../docs/framework/data/adonet/navigation-property.md)  
  
 [Vlastnost](../../../../docs/framework/data/adonet/property.md)  
  
 [omezení referenční integrity](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)  
  
## <a name="see-also"></a>Viz také  
 [Nástroje modelu ADO.NET Entity Data Model](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [Přehled souboru EDMX](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [Specifikace CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)
