---
title: "Načtení dat z čtečka čipových karet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9e9f934d6bff2c9ff3733551bca89b43920f3104
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="load-data-from-a-reader"></a>Načtení dat z čtečka čipových karet
Pokud dokument XML je načíst pomocí <xref:System.Xml.XmlDocument.Load%2A> metoda a parametr <xref:System.Xml.XmlReader>, jsou rozdíly v chování, k níž dojde v porovnání s chování načítání dat z jiných formátů. Pokud čtečka je ve stavu počáteční <xref:System.Xml.XmlDocument.Load%2A> využívá celý obsah ze čtečky a vytvoří kódu XML modelu DOM (Document Object) ze všech dat ve čtečce.  
  
 Pokud čtečka je už umístěna v uzlu někde v dokumentu a čtečka se pak předá do <xref:System.Xml.XmlDocument.Load%2A> metody <xref:System.Xml.XmlDocument.Load%2A> se pokusí přečíst na aktuální uzel a všechny uzly na stejné úrovni, až koncovou značku, která zavře aktuální hloubka do paměti. Úspěch pokusu o <xref:System.Xml.XmlDocument.Load%2A> závisí na uzlu, který je čtečka na při pokusu o zatížení jako <xref:System.Xml.XmlDocument.Load%2A> ověřuje, že je ve správném formátu XML ze čtečky. Pokud není ve správném formátu XML <xref:System.Xml.XmlDocument.Load%2A> vyvolá výjimku. Například následující sada uzlů obsahovat dva elementy úrovni kořenového adresáře, kód XML není ve správném formátu, a <xref:System.Xml.XmlDocument.Load%2A> vyvolá výjimku.  
  
-   Uzel komentáře, za nímž následuje do uzlu Element, za nímž následuje do uzlu Element, za nímž následuje do EndElement uzlu.  
  
 Následující sada uzlů vytvoří neúplné DOM, protože neexistuje žádný element kořenové úrovni.  
  
-   Uzel komentáře, za nímž následuje uzel komentáře, za nímž následuje do uzlu EndElement ProcessingInstruction uzel.  
  
 To nevyvolá výjimku a načíst data. Můžete přidat kořenový element do horní části tyto uzly a vytvořit ve správném formátu XML, který lze uložit bez chyby.  
  
 Pokud čtečka je umístěn na uzel typu list, který je neplatný pro kořenové úrovni dokumentu (například bílé místo nebo atributu uzlu), čtečky pokračovat ve čtení, dokud je umístěný na uzel, který lze použít pro kořenový adresář. Dokument začíná načítání v tomto okamžiku.  
  
 Ve výchozím nastavení <xref:System.Xml.XmlDocument.Load%2A> neověřuje, zda je platný, pomocí definice typu dokumentu (DTD) nebo ověřování schématu XML. Pouze ověřuje, zda je soubor XML ve správném formátu. Aby k ověření, je potřeba vytvořit <xref:System.Xml.XmlReader> pomocí <xref:System.Xml.XmlReaderSettings> třídy. <xref:System.Xml.XmlReader> Třídy můžete vynutit pomocí DTD nebo schéma definition language (XSD) schématu ověření. <xref:System.Xml.ValidationType> Vlastnost <xref:System.Xml.XmlReaderSettings> Určuje třídu zda <xref:System.Xml.XmlReader> instance vynucuje ověřování. Další informace o ověření XML data, najdete v části poznámky <xref:System.Xml.XmlReader> stránka s referencemi k.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
