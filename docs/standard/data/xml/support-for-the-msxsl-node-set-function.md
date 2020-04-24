---
title: Podpora pro funkci msxsl:node-set()
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
ms.openlocfilehash: 5022b298cb20796edbc54e951d8b06043697d832
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155591"
---
# <a name="support-for-the-msxslnode-set-function"></a>Podpora pro funkci msxsl:node-set()
`msxsl:node-set` Funkce umožňuje převést fragment stromu výsledků na sadu uzlů. Výsledná sada uzlů vždy obsahuje jeden uzel a je kořenovým uzlem stromu.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Třída je zastaralá v .NET Framework 2,0. Transformace XSLT (Extensible Stylesheet Language) můžete použít k <xref:System.Xml.Xsl.XslCompiledTransform> transformaci pomocí třídy. Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 `msxsl:node-set` Funkce umožňuje převést fragment stromu výsledků na sadu uzlů. Výsledná sada uzlů vždy obsahuje jeden uzel a je kořenovým uzlem stromu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `$var` je proměnná, která je stromem uzlu v šabloně stylů. Příkaz for-each v kombinaci s `node-set` funkcí umožňuje uživateli iterovat v rámci tohoto stromu uzlů jako sadu uzlů.  
  
## <a name="nodesetxsl"></a>uzlů. xsl  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">
                <author><xsl:value-of select="@author"/></author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a>Výstup  
 Výstup transformace je  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a>Viz také

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
