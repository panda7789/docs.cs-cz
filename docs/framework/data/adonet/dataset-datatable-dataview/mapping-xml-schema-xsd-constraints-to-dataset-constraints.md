---
title: "Omezení (XSD) schématu XML mapování k omezení datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f403dc974e4fe67d239688f587061cd23a8deff6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>Omezení (XSD) schématu XML mapování k omezení datové sady
Jazyk definice schématu XML (XSD) umožňuje omezení ho zadat na elementy a atributy, které ho definuje. Při mapování schématu XML na relační schéma v <xref:System.Data.DataSet>, schématu XML omezení jsou namapované na příslušné relační omezení tabulek a sloupců v rámci **datovou sadu**.  
  
 Tato část popisuje mapování schématu XML následující omezení:  
  
-   Omezení jedinečnosti zadán pomocí **jedinečný** elementu.  
  
-   Omezení klíč zadaný pomocí **klíč** elementu.  
  
-   Omezení keyref zadán pomocí **keyref** elementu.  
  
 Pomocí omezení k elementu nebo atributu zadejte určitá omezení na hodnotách element v žádné instanci dokumentu. Například klíče omezení **CustomerID** podřízený prvek **zákazníka** element ve schématu znamená, že hodnoty **CustomerID** podřízený element musí být v žádné instanci dokumentu jedinečný a že hodnoty null nejsou povolené.  
  
 Omezení lze zadat také mezi elementy a atributy v dokumentu, aby bylo možné vytvořit vztah v tomto dokumentu. Klíč a keyref omezení lze ve schématu zadejte omezení v tomto dokumentu, výsledkem je vztah mezi dokumentu elementů a atributů.  
  
 Proces mapování převede těchto omezení schématu odpovídající omezení tabulky v rámci vytvořili **datovou sadu**.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje elementy schématu XML použitý k vytvoření jedinečné omezení **datovou sadu**.  
  
 [Mapování klíčových omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje elementy schématu XML použitý k vytvoření klíče omezení (kde hodnoty null nejsou povolené jedinečná omezení) **datovou sadu**.  
  
 [Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Popisuje elementy schématu XML použitý k vytvoření keyref omezení (cizí klíč) **datovou sadu**.  
  
## <a name="related-sections"></a>Související oddíly  
 [Odvozování relační struktury datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 Popisuje relační struktura nebo schéma z **datovou sadu** vytvořený z schématu XSD.  
  
 [Generování relací datové sady ze schématu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 Popisuje elementy schématu XML použitý k vytvoření relace mezi sloupci tabulky v **datovou sadu**.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
