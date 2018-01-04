---
title: "Schéma kolekci XmlSchemaCollection kompilace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c891736534741d1d3d3edb93d75d9f191c2dd573
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="xmlschemacollection-schema-compilation"></a>Schéma kolekci XmlSchemaCollection kompilace
**Kolekci XmlSchemaCollection** je do mezipaměti nebo knihovny, kam můžete ukládat a ověřit XML-Data Reduced (XDR) a schématu XML schémata definition language (XSD). **Kolekci XmlSchemaCollection** zlepšuje výkon díky ukládání do mezipaměti schémata v paměti místo k nim přistupovat ze souboru nebo adresa URL.  
  
> [!NOTE]
>  I když **kolekci XmlSchemaCollection** třída ukládá XDR schémata a schémat XML, všechny metody a vlastnosti, která přebírá nebo vrátí **XmlSchema** objekt podporuje pouze schémat XML.  
  
> [!IMPORTANT]
>  <xref:System.Xml.Schema.XmlSchemaCollection> Třída je zastaralá a nahradila s <xref:System.Xml.Schema.XmlSchemaSet> třídy. Další informace o <xref:System.Xml.Schema.XmlSchemaSet> najdete třída [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).  
  
## <a name="add-schemas-to-the-collection"></a>Přidat do kolekce schémat.  
 Schémata jsou načteny do kolekce pomocí **přidat** metodu **kolekci XmlSchemaCollection**, po kterých je přidružen identifikátor URI oboru názvů schématu. Schémat XML identifikátor URI oboru názvů bude obvykle cílový obor názvů pro schéma. U XDR schémat identifikátor URI oboru názvů je že obor názvů zadán, pokud bylo schéma přidat do kolekce.  
  
## <a name="check-for-a-schema-in-the-collection"></a>Zkontrolujte schéma v kolekci  
 Můžete zkontrolovat, zda schéma je v kolekci pomocí **obsahuje** metoda. **Obsahuje** metoda přebírá buď **XmlSchema** objektu (pro jenom schémata XML) nebo řetězec představující identifikátor URI oboru názvů přidružené schéma (pro schémat XML a XDR schémat).  
  
## <a name="retrieve-a-schema-from-the-collection"></a>Načíst schéma z kolekce  
 Můžete načíst schéma z kolekce pomocí **položky** vlastnost. **Položky** vlastnost přebírá řetězec představující obor názvů URI přidružený schématu, obvykle jeho cílový obor názvů a vrátí **XmlSchema** objektu. **Položky** vlastnost se vztahuje pouze na schémata XML. Vrácená hodnota je vždy odkaz s hodnotou null pro schémata XDR, protože nemají objektový model, který je k dispozici.  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>Ověření pomocí kolekci XmlSchemaCollection dokumentů XML  
 Můžete ověřit instance dokumentu XML pomocí **kolekci XmlSchemaCollection** vytvořením **kolekci XmlSchemaCollection** objekt, přidávání vaší schémata do kolekce a nastavení **schémat.**  vlastnost **třídy XmlValidatingReader** přiřadit vytvořený **kolekci XmlSchemaCollection** k **třídy XmlValidatingReader**.  
  
### <a name="improved-performance"></a>Lepší výkon  
 Se doporučuje, pokud ověřujete více než jeden dokument pro stejné schéma, že používáte **kolekci XmlSchemaCollection** protože poskytuje lepší výkon pomocí ukládání do mezipaměti schémata v paměti.  
  
 Následující příklad kódu vytvoří **kolekci XmlSchemaCollection** objekt, přidá do kolekce schémat a nastaví **schémata** vlastnost.  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a>Viz také  
 [Ověření XDR s třídou XmlSchemaCollection](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [Ověření schématu XML (XSD) s třídou XmlSchemaCollection](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
