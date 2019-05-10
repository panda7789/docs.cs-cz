---
title: Úprava uzlů, obsahu a hodnot v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 976c34d72f9fcc89193658e50727a0ad365f2dd8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647892"
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>Úprava uzlů, obsahu a hodnot v dokumentu XML
Existuje mnoho způsobů můžete upravit uzly a obsah v dokumentu. Můžete:  
  
- Změňte hodnotu vlastnosti uzlů pomocí <xref:System.Xml.XmlNode.Value%2A> vlastnost.  
  
- Upravte celou sadu uzlů nahrazením uzly nové uzly. To se provádí pomocí <xref:System.Xml.XmlNode.InnerXml%2A> vlastnost.  
  
- Nahraďte existující uzly pomocí nových uzlů <xref:System.Xml.XmlNode.RemoveChild%2A> metody.  
  
- Přidat další znaky uzly, které dědí <xref:System.Xml.XmlCharacterData> pomocí <xref:System.Xml.XmlCharacterData.AppendData%2A>, <xref:System.Xml.XmlCharacterData.InsertData%2A>, nebo <xref:System.Xml.XmlCharacterData.ReplaceData%2A> metody.  
  
- Upravte obsah tak, že odeberete rozsahu znaků pomocí <xref:System.Xml.XmlCharacterData.DeleteData%2A> metodu na typy uzlů, které dědí z <xref:System.Xml.XmlCharacterData>.  
  
 Jednoduchý postup pro změnu hodnoty uzlu je použití `node.Value = "new value";`. V následující tabulce jsou uvedeny typy uzlů, které tento jediný řádek kódu funguje na a přesně je změnit, jaká data pro tento typ uzlu.  
  
|Typ uzlu|Změny dat|  
|---------------|------------------|  
|Atribut|Hodnota atributu.|  
|CDATASection|Obsah CDATASection.|  
|Komentář|Obsah komentář.|  
|ProcessingInstruction|Obsah, s výjimkou cíl.|  
|Text|Obsah textu.|  
|XmlDeclaration|Obsah prohlášení, s výjimkou `<?xml` a `?>` značek.|  
|Prázdné znaky|Hodnota prázdné znaky. Můžete nastavit hodnotu na jednu z 4 znaky rozpoznaný prázdné znaky XML: prostor, karty, CR nebo LF.|  
|SignificantWhitespace|Hodnota významných mezer. Můžete nastavit hodnotu na jednu z 4 znaky rozpoznaný prázdné znaky XML: prostor, karty, CR nebo LF.|  
  
 Jakýkoli typ uzlu nejsou uvedené v tabulce není typem platný uzel. Chcete-li nastavit hodnotu na. Nastavení hodnoty na žádném vyvolá jiný typ uzlu <xref:System.InvalidOperationException>.  
  
 <xref:System.Xml.XmlNode.InnerXml%2A> Vlastnost se změní z podřízených uzlů pro aktuální uzel kódu. Nastavení této vlastnosti nahradí podřízených uzlů obsah analyzovaný daný řetězec. Analýza provádí v rámci aktuálního kontextu oboru názvů. Kromě toho <xref:System.Xml.XmlNode.InnerXml%2A> odebere deklarace oboru názvů redundantní. Operace jako výsledek, mnoho vyjmutí a vložení nezvětšily velikost dokumentu pomocí deklarace oboru názvů redundantní. Příklad kódu znázorňuje vliv obory názvů <xref:System.Xml.XmlNode.InnerXml%2A> operace, najdete v článku <xref:System.Xml.XmlDocument.InnerXml%2A> vlastnost.  
  
 Při použití <xref:System.Xml.XmlCharacterData.ReplaceData%2A> a <xref:System.Xml.XmlNode.RemoveChild%2A> metody, metody, vrátí se uzel odebrán nebo nahrazen. Tento uzel můžete pak obnovena někde jinde v XML Document Object Model (DOM). <xref:System.Xml.XmlCharacterData.ReplaceData%2A> Metoda provádí dva ověřovací kontroly v uzlu se vloží do dokumentu. První kontrola zajistí, že uzlu se mění na podřízený uzel, který může obsahovat podřízené uzly typu. Druhé kontroly zajistí, že uzel vloženého není nadřazena uzlu, na který ho se mění na podřízený. Některá z těchto porušení podmínek vyvolá <xref:System.InvalidOperationException>.  
  
 Je možné přidat nebo odebrat podřízené jen pro čtení z uzlu, které lze upravovat. Ale vyvolá pokusy o upravit samotný uzel jen pro čtení <xref:System.InvalidOperationException>. Příkladem je úprava podřízených položek <xref:System.Xml.XmlEntityReference> uzlu. Podřízené objekty jsou jen pro čtení a nelze upravovat. Žádný pokus upravit je vyvolá <xref:System.InvalidOperationException>.  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
