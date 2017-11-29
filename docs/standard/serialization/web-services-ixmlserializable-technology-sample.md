---
title: "Ukázka IXmlSerializable technologie webové služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0202d3f1-a50b-427d-a5bb-79208b8f1c22
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 72c7e9e1cbf47dd54726a16ddeb58a193d62dc31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="web-services-ixmlserializable-technology-sample"></a>Ukázka IXmlSerializable technologie webové služby
[Stažení ukázky](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/IXmlSerializable.zip.exe)  
  
 Tento příklad ukazuje, jak používat <xref:System.Xml.Serialization.IXmlSerializable> k řízení serializace vlastních typů ve webové služby ASP.NET.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>K vytvoření vzorku pomocí sady Visual Studio  
  
1.  Otevřete [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] a vyberte **nový web** z **souboru** nabídky.  
  
2.  V levém podokně **nový web** dialogovém okně, vyberte požadovaný programovací jazyk a pak v pravém podokně vyberte **webovou službu ASP.NET**.  
  
3.  Typ **IXmlSerializable** jako název nové webové služby.  
  
4.  V okně Průzkumníku řešení klikněte pravým tlačítkem na ikonu pro Service.asmx a vyberte **odstranit**; tento krok opakujte pro soubor codebehind Service.asmx.  
  
5.  Klikněte pravým tlačítkem na projekt adresář a zaškrtněte možnost **přidat existující položku**. V dialogovém okně přejděte na podadresáři služby adresáře konkrétní jazyk.  
  
6.  Vyberte Service.asmx a poté opakujte tento krok pro soubor codebehind Service.asmx.  
  
7.  Otevřít [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] a přejděte do adresáře, který obsahuje IXmlSerializable adresář, který jste vytvořili v kroku 3 výše.  
  
8.  Klikněte pravým tlačítkem myši na ikonu pro IXmlSerializable adresář a vyberte **sdílení a zabezpečení**.  
  
9. Na kartě Sdílení na webu vyberte **Sdílejte tuto složku**a potvrďte výchozí nastavení, včetně názvu IXmlSerializable.  
  
10. Click **OK**.  
  
### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete okno prohlížeče a vyberte jeho adresa.  
  
2.  Typ **http://localhost/IXmlSerializable/Service.asmx**.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization>  
 <xref:System.Xml.XmlConvert>  
 <xref:System.Xml.XmlQualifiedName>  
 <xref:System.Xml.XmlReader>  
 <xref:System.Xml.Schema.XmlSchema>  
 <xref:System.Xml.Schema.XmlSchemaSet>  
 <xref:System.Xml.XmlUrlResolver>  
 <xref:System.Xml.XmlWriter>
