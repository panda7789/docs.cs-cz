---
title: Kompilace schématu XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7b6ea782020dde83aa7d59be8ec3058a27075ad
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677694"
---
# <a name="xmlschemacollection-schema-compilation"></a>Kompilace schématu XmlSchemaCollection
**Třídou XmlSchemaCollection** mezipaměti nebo knihovny, kde můžete ukládat a ověřit XML-Data Reduced (XDR) a schéma XML definice jazyk (XSD) schémata. **Kolekci XmlSchemaCollection** zvyšuje výkon díky ukládání do mezipaměti schémat v paměti namísto se k nim dostanete ze souboru nebo adresy URL.  
  
> [!NOTE]
>  I když **třídou XmlSchemaCollection** třída uchovává XDR schémat a schémat XML, všechny metody a vlastnosti, která přijímá nebo vrátí **XmlSchema** objekt podporuje pouze schémata XML.  
  
> [!IMPORTANT]
>  <xref:System.Xml.Schema.XmlSchemaCollection> Třída je zastaralá a bylo nahrazeno tématem <xref:System.Xml.Schema.XmlSchemaSet> třídy. Další informace o <xref:System.Xml.Schema.XmlSchemaSet> třídy viz [XmlSchemaSet pro kompilaci schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).  
  
## <a name="add-schemas-to-the-collection"></a>Přidání do kolekce schémat  
 Schémata jsou načteny do kolekce pomocí **přidat** metoda **třídou XmlSchemaCollection**, po kterém schéma je přidružen k oboru názvů identifikátoru URI. Schémat XML obor názvů URI bude obvykle cílový obor názvů pro schéma. Pro schémata XDR identifikátor URI oboru názvů je že obor názvů určený při schématu byl přidán do kolekce.  
  
## <a name="check-for-a-schema-in-the-collection"></a>Vyhledat schéma v kolekci  
 Můžete zkontrolovat, jestli schéma je v kolekci pomocí **obsahuje** metoda. **Obsahuje** metoda přebírá buď **XmlSchema** objekt (pouze schémata XML) nebo řetězec představující obor názvů URI přidružený k schématu (pro schémata schémat XML a XDR).  
  
## <a name="retrieve-a-schema-from-the-collection"></a>Načíst schéma z kolekce  
 Můžete načíst schéma z kolekce pomocí **položky** vlastnost. **Položky** vlastnost přebírá řetězec představující obor názvů URI přidružený k schématu, obvykle jeho cílový obor názvů a vrátí **XmlSchema** objektu. **Položky** vlastnost se vztahuje pouze na schématech XML. Vrácená hodnota je vždy odkaz s hodnotou null pro schémata XDR, protože nemají objekt modelu, který je k dispozici.  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a>Ověření XML dokumenty v kolekci XmlSchemaCollection  
 Můžete ověřit v instanci dokumentu XML pomocí **třídou XmlSchemaCollection** tak, že vytvoříte **třídou XmlSchemaCollection** objektu, přidání vašeho schémata do kolekce a nastavení **schémata**  vlastnost **objekt XmlValidatingReader** přiřadit vytvořený **třídou XmlSchemaCollection** k **objekt XmlValidatingReader**.  
  
### <a name="improved-performance"></a>Vylepšení výkonu  
 Doporučuje, pokud se ověření více než jeden dokument pomocí stejné schéma, že používáte **třídou XmlSchemaCollection** vzhledem k tomu, že poskytuje lepší výkon díky ukládání do mezipaměti schémat v paměti.  
  
 Následující příklad kódu vytvoří **třídou XmlSchemaCollection** objekt, přidá do kolekce schémat a nastaví **schémata** vlastnost.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Ověření XDR s třídou XmlSchemaCollection](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
- [Ověření schématu XML (XSD) s třídou XmlSchemaCollection](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
