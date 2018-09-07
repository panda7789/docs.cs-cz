---
title: Načtení dat z čtečky
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 55756092f086de47c4b2acb8f147ca3ab231abe1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44068921"
---
# <a name="load-data-from-a-reader"></a>Načtení dat z čtečky
Pokud dokument XML je načtené pomocí možnosti <xref:System.Xml.XmlDocument.Load%2A> metoda a parametr <xref:System.Xml.XmlReader>, existují rozdíly v chování, která nastane v porovnání s chování načítání dat z jiných formátů. Pokud čtečka nachází ve stavu počáteční <xref:System.Xml.XmlDocument.Load%2A> využívá celý obsah ze čtečky a sestavení XML Document Object Model (DOM) z všechna data ve čtečce.  
  
 Pokud ukazatel čtení je již umístěný na uzlu někde v dokumentu a čtečky je pak předán <xref:System.Xml.XmlDocument.Load%2A> metody <xref:System.Xml.XmlDocument.Load%2A> se pokusí přečíst aktuální uzel a všechny na stejné úrovni, až koncovou značku, která ukončí aktuální hloubka do paměti. Úspěch pokusu o <xref:System.Xml.XmlDocument.Load%2A> závisí na uzlu, který je čtečka na při pokusu o zatížení, jako <xref:System.Xml.XmlDocument.Load%2A> ověří, jestli je ve správném formátu XML ze čtečky. Pokud kód XML není ve správném formátu, <xref:System.Xml.XmlDocument.Load%2A> vyvolá výjimku. Například následující sadu uzlů obsahovat dva prvky na kořenové úrovni serveru, kód XML není ve správném formátu, a <xref:System.Xml.XmlDocument.Load%2A> vyvolá výjimku.  
  
-   Uzel komentáře, za nímž následuje uzlu elementu, za nímž následuje uzlu elementu, za nímž následuje uzlu EndElement.  
  
 Následující sada uzlů vytvoří neúplné modelu DOM, protože neexistuje žádný element na kořenové úrovni.  
  
-   Uzel komentáře, za nímž následuje za nímž následuje uzel komentáře, za nímž následuje uzlu EndElement ProcessingInstruction uzlu.  
  
 Nevyvolá výjimku a načíst data. Můžete přidat kořenový element k hornímu okraji tyto uzly a vytvořit ve správném formátu XML, který můžete uložit bez chyb.  
  
 Pokud ukazatel čtení je umístěný na uzel typu list, který není platný pro kořenové úrovni dokumentu (například bílého místa nebo atribut uzlu), čtečky pokračovat ve čtení, dokud je umístěn na uzlu, který lze použít pro kořen. Dokument začíná načítání v tomto okamžiku.  
  
 Ve výchozím nastavení <xref:System.Xml.XmlDocument.Load%2A> neověřuje, zda je platný, pomocí definice typu dokumentu (DTD) nebo ověřování schématu XML. Pouze ověří, zda je soubor XML ve správném formátu. Aby dojde k ověření, je potřeba vytvořit <xref:System.Xml.XmlReader> pomocí <xref:System.Xml.XmlReaderSettings> třídy. <xref:System.Xml.XmlReader> Třída může vynutit ověřování pomocí DTD nebo schématu definice jazyk (XSD) schématu. <xref:System.Xml.ValidationType> Vlastnost na <xref:System.Xml.XmlReaderSettings> třída určuje, zda <xref:System.Xml.XmlReader> instance vynucuje ověřování. Další informace o ověřování XML dat, najdete v části poznámky <xref:System.Xml.XmlReader> referenční stránce.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
