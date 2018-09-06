---
title: 'Postupy: provedení transformace XSLT pomocí sestavení'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76ee440b-d134-4f8f-8262-b917ad6dcbf6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef0d47ae18b8bdd3f1d49a20937b65e9872ab551
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892344"
---
# <a name="how-to-perform-an-xslt-transformation-by-using-an-assembly"></a>Postupy: provedení transformace XSLT pomocí sestavení
Kompilátor XSLT (xsltc.exe) zkompiluje šablon stylů XSLT a generuje sestavení. Sestavení mohou být předány přímo do <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> metody.  
  
### <a name="to-copy-the-xml-and-xslt-files-to-your-local-computer"></a>Kopírování souborů XML a XSLT do místního počítače  
  
-   Zkopírujte soubor XSLT do místního počítače a pojmenujte ho Transform.xsl.  
  
    ```xml  
    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
      xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
      xmlns:user="urn:my-scripts">  
      <msxsl:script language="C#" implements-prefix="user">  
        <![CDATA[  
      public string discount(string price){  
        char[] trimChars = { '$' };  
        //trim leading $, convert price to type double  
        double discount_value = Convert.ToDouble(price.TrimStart(trimChars));  
        //apply 10% discount and round appropriately  
        discount_value = .9*discount_value;  
        //convert value to decimal and format as currency  
        string discount_price = discount_value.ToString("C");  
        return discount_price;  
      }  
      ]]>  
      </msxsl:script>  
      <xsl:template match="catalog">  
        <html>  
          <head></head>  
          <body>  
            <table border="1">  
              <tr>  
                <th align="left">Title</th>  
                <th align="left">Author</th>  
                <th align="left">Genre</th>  
                <th align="left">Publish Date</th>  
                <th align="left">Price</th>  
              </tr>  
              <xsl:for-each select="book">  
                <tr>  
                  <td>  
                    <xsl:value-of select="title"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="author"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="genre"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="publish_date"/>  
                  </td>  
                  <xsl:choose>  
                    <xsl:when test="genre = 'Fantasy'">  
                      <td>  
                        <xsl:value-of select="user:discount(price)"/>  
                      </td>  
                    </xsl:when>  
                    <xsl:otherwise>  
                      <td>  
                        <xsl:value-of select="price"/>  
                      </td>  
                    </xsl:otherwise>  
                  </xsl:choose>  
                </tr>  
              </xsl:for-each>  
            </table>  
          </body>  
        </html>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
-   Zkopírujte soubor XML do místního počítače a pojmenujte ho `books.xml`.  
  
    ```xml  
    <?xml version="1.0"?>  
    <catalog>  
       <book id="bk101">  
          <author>Gambardella, Matthew</author>  
          <title>XML Developer's Guide</title>  
          <genre>Computer</genre>  
          <price>$44.95</price>  
          <publish_date>2000-10-01</publish_date>  
       </book>  
       <book id="bk102">  
          <author>Ralls, Kim</author>  
          <title>Midnight Rain</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-12-16</publish_date>  
       </book>  
       <book id="bk103">  
          <author>Corets, Eva</author>  
          <title>Maeve Ascendant</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-11-17</publish_date>  
       </book>  
       <book id="bk106">  
          <author>Randall, Cynthia</author>  
          <title>Lover Birds</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-09-02</publish_date>  
       </book>  
       <book id="bk107">  
          <author>Thurman, Paula</author>  
          <title>Splish Splash</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-11-02</publish_date>  
       </book>  
    </catalog>  
    ```  
  
### <a name="to-compile-the-style-sheet-with-the-script-enabled"></a>Pro kompilaci šablony stylů se skriptem povolena.  
  
1.  Spuštěním následujícího příkazu z příkazového řádku vytvoří dvě sestavení s názvem `Transform.dll` a `Transform_Script1.dll` (Toto je výchozí chování. Pokud není uvedeno jinak, název třídy a sestavení výchozím názvem hlavní šablony stylů):  
  
    ```  
    xsltc /settings:script+ Transform.xsl  
    ```  
  
 Následující příkaz k transformaci explicitně nastaví název třídy:  
  
```  
xsltc /settings:script+ /class:Transform Transform.xsl  
```  
  
### <a name="to-include-the-compiled-assembly-as-a-reference-when-you-compile-your-code"></a>Chcete-li zahrnout zkompilovaného sestavení jako odkaz při kompilaci kódu.  
  
1.  Můžete zahrnout sestavení v sadě Visual Studio tak, že přidáte odkaz v Průzkumníku řešení nebo z příkazového řádku.  
  
2.  Pro příkazový řádek s jazykem C# použijte následující:  
  
    ```  
    csc myCode.cs /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
3.  Pro příkazový řádek s jazykem Visual Basic použijte tento příkaz  
  
    ```  
    vbc myCode.vb /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
### <a name="to-use-the-compiled-assembly-in-your-code"></a>Pro použití ve vašem kódu zkompilovaného sestavení.  
  
1.  Následující příklad ukazuje, jak provedení transformace XSLT pomocí zkompilované šablony stylů.  
  
 [!code-csharp[XslTransform_XSLTC#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslTransform_XSLTC/CS/XslTransform_XSLTC.cs#1)]
 [!code-vb[XslTransform_XSLTC#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslTransform_XSLTC/VB/XslTransform_XSLTC.vb#1)]  
  
 Chcete-li propojit dynamicky kompilovaných sestavení, nahraďte  
  
```  
xslt.Load(typeof(Transform))  
```  
  
 with  
  
```  
xslt.Load(System.Reflection.Assembly.Load("Transform").GetType("Transform"))  
```  
  
 v předchozím příkladu. Další informace o metodě Assembly.Load naleznete v tématu <xref:System.Reflection.Assembly.Load%2A>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Xsl.XslCompiledTransform>  
- [Kompilátor XSLT (xsltc.exe)](../../../../docs/standard/data/xml/xslt-compiler-xsltc-exe.md)  
- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [Sestavování pomocí programu csc.exe v příkazovém řádku](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
