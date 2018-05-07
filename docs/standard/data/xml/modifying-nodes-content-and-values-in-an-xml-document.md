---
title: Úprava uzlů, obsah a hodnoty v dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 761773e0-db72-4986-b9f5-a522213d8397
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 716270450a5f0ede545ffcbd906b0a42f547c20f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="modifying-nodes-content-and-values-in-an-xml-document"></a>Úprava uzlů, obsah a hodnoty v dokumentu XML
Existuje mnoho způsobů můžete upravit uzly a obsah v dokumentu. Můžeš:  
  
-   Změňte hodnotu uzlů pomocí <xref:System.Xml.XmlNode.Value%2A> vlastnost.  
  
-   Upravte celá sada uzlů nahrazením uzly nových uzlů. To se provádí pomocí <xref:System.Xml.XmlNode.InnerXml%2A> vlastnost.  
  
-   Nahraďte stávající uzly nových uzlů pomocí <xref:System.Xml.XmlNode.RemoveChild%2A> metoda.  
  
-   Přidat další znaky na uzly, které dědí od <xref:System.Xml.XmlCharacterData> pomocí <xref:System.Xml.XmlCharacterData.AppendData%2A>, <xref:System.Xml.XmlCharacterData.InsertData%2A>, nebo <xref:System.Xml.XmlCharacterData.ReplaceData%2A> metody.  
  
-   Upravit obsah tím, že odebere rozsah znaků pomocí <xref:System.Xml.XmlCharacterData.DeleteData%2A> metodu pro uzel typy, které dědí od <xref:System.Xml.XmlCharacterData>.  
  
 Jednoduché technik pro změnu hodnoty uzlu je použít `node.Value = "new value";`. Následující tabulka uvádí typy uzlů, které tento jediný řádek kódu na funguje a přesně se mění jaká data pro tento typ uzlu.  
  
|Typ uzlu|Změnit data|  
|---------------|------------------|  
|Atribut|Hodnota atributu.|  
|CDATASection|Obsah CDATASection.|  
|Komentář|Obsah komentář.|  
|ProcessingInstruction|Obsah, s výjimkou cíl.|  
|Text|Obsah textu.|  
|XmlDeclaration|Prohlášení, s výjimkou `<?xml` a `?>` značek.|  
|Prázdné znaky|Hodnota prázdné znaky. Můžete nastavit hodnotu na jednu z čtyři rozpoznaný prázdné znaky XML: mezera, tabulátor, CR nebo LF.|  
|SignificantWhitespace|Hodnota významné prázdné znaky. Můžete nastavit hodnotu na jednu z čtyři rozpoznaný prázdné znaky XML: mezera, tabulátor, CR nebo LF.|  
  
 Žádný typ uzlu není uvedený v tabulce není platný uzel typu nastavte hodnotu na. Nastavení hodnoty na žádný jiný typ uzlu vyvolá <xref:System.InvalidOperationException>.  
  
 <xref:System.Xml.XmlNode.InnerXml%2A> Změny vlastností kód podřízené uzly pro aktuální uzel. Nastavení této vlastnosti nahradí Analyzovaná obsah daný řetězec podřízených uzlů. Analýza ve vyrovnaném se provádí v aktuálním kontextu oboru názvů. Kromě toho <xref:System.Xml.XmlNode.InnerXml%2A> odebere deklarace redundantní oborů názvů. Jako výsledek, množství vyjímání a vkládání operations není zvětšete velikost vašeho dokumentu s deklaracemi redundantní oboru názvů. Příklad kódu zobrazuje účinku obory názvů na <xref:System.Xml.XmlNode.InnerXml%2A> operace, najdete v článku <xref:System.Xml.XmlDocument.InnerXml%2A> vlastnost.  
  
 Při použití <xref:System.Xml.XmlCharacterData.ReplaceData%2A> a <xref:System.Xml.XmlNode.RemoveChild%2A> metody, metody vrátí uzel nahrazené nebo odebrané. Tento uzel můžete pak znovu vložit někde jinak v XML dokumentu objektu modelu (DOM). <xref:System.Xml.XmlCharacterData.ReplaceData%2A> Metoda nemá dvě ověřovací kontroly na uzlu vkládání do dokumentu. První kontrola zajistí, že uzel se stává stále podřízený uzel, který může mít podřízené uzly daného typu. Druhý kontrola zajistí, že vkládání uzel není nadřazeným uzlu, který ho se stává stále podřízenou. Jedna z těchto bychom při tom porušili podmínky vrátí <xref:System.InvalidOperationException>.  
  
 Je možné přidat nebo odebrat podřízený jen pro čtení z uzlu, který lze upravovat. Však vyvolá pokusí změnit samotný uzel jen pro čtení <xref:System.InvalidOperationException>. Příkladem je úprava podřízené objekty daného <xref:System.Xml.XmlEntityReference> uzlu. Podřízené objekty jsou jen pro čtení a nelze jej změnit. Žádné pokusí změnit jejich vyvolává <xref:System.InvalidOperationException>.  
  
## <a name="see-also"></a>Viz také  
 [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
