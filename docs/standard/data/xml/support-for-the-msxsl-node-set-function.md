---
title: Podpora pro funkci msxsl:node-set()
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
ms.openlocfilehash: b9603f6c910e8e29309618c8e01e283c28ae2bff
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710125"
---
# <a name="support-for-the-msxslnode-set-function"></a>Podpora pro funkci msxsl:node-set()
Funkce `msxsl:node-set` umožňuje převést fragment stromu výsledků na sadu uzlů. Výsledná sada uzlů vždy obsahuje jeden uzel a je kořenovým uzlem stromu.  
  
> [!NOTE]
> Třída <xref:System.Xml.Xsl.XslTransform> je v .NET Framework 2,0 zastaralá. Pomocí třídy <xref:System.Xml.Xsl.XslCompiledTransform> můžete provádět transformace XSLT (Extensible Stylesheet Language). Další informace najdete v tématu [použití třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) a [migrace z třídy XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Funkce `msxsl:node-set` umožňuje převést fragment stromu výsledků na sadu uzlů. Výsledná sada uzlů vždy obsahuje jeden uzel a je kořenovým uzlem stromu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `$var` je proměnná, která je stromem uzlů v šabloně stylů. Příkaz for-each v kombinaci s funkcí `node-set` umožňuje uživateli iterovat v rámci tohoto stromu uzlů jako sadu uzlů.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Třída XslTransform implementuje procesor XSLT](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
