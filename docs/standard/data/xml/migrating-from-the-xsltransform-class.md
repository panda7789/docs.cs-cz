---
title: Migrace z třídy XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d8b8c21af8ca0a21d97e8246ad82c42aaaf4974
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45971965"
---
# <a name="migrating-from-the-xsltransform-class"></a>Migrace z třídy XslTransform
Architektura XSLT byla přepracována v [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] release. <xref:System.Xml.Xsl.XslTransform> Třídy nahradila ji <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
 Následující části popisují některé hlavní rozdíly mezi <xref:System.Xml.Xsl.XslCompiledTransform> a <xref:System.Xml.Xsl.XslTransform> třídy.  
  
## <a name="performance"></a>Výkon  
 <xref:System.Xml.Xsl.XslCompiledTransform> Třída zahrnuje mnoho vylepšení výkonu. Zkompiluje nový procesoru XSLT šablony stylů XSLT na běžné mezilehlého formátu, podobně jako na modul CLR (CLR) nemá pro jiných programovacích jazycích. Jakmile je zkompilován šablony stylů, může do mezipaměti a znovu použít.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Třída také obsahuje další optimalizace, které usnadňují mnohem rychlejší než <xref:System.Xml.Xsl.XslTransform> třídy.  
  
> [!NOTE]
>  I když celkový výkon <xref:System.Xml.Xsl.XslCompiledTransform> třída je lepší, než <xref:System.Xml.Xsl.XslTransform> třídy, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslCompiledTransform> třídy můžou provádět více pomalu než <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslTransform> třída první, když je volán na transformaci. Je to proto musí být kompilován soubor XSLT, předtím, než je načten. Další informace najdete v následujícím blogovém příspěvku: [XslCompiledTransform pomalejší než XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="security"></a>Zabezpečení  
 Ve výchozím nastavení <xref:System.Xml.Xsl.XslCompiledTransform> třídy zakáže podporu pro XSLT `document()` funkce a vložené skriptování. Tyto funkce se dá nastavit tak, že vytvoříte <xref:System.Xml.Xsl.XsltSettings> objekt, který má funkce povolena a předá se <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metody. Následující příklad ukazuje, jak povolit skriptování a provedení transformace XSLT.  
  
 [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
 [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
 Další informace najdete v tématu [aspekty zabezpečení XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md).  
  
## <a name="new-features"></a>Nové funkce  
  
### <a name="temporary-files"></a>Dočasné soubory  
 Dočasné soubory jsou vygenerovány někdy během XSLT zpracování. Pokud šablona stylů obsahuje bloky kódu skriptu, nebo pokud je kompilován nastavení ladění je nastavená na hodnotu true, dočasné soubory může vytvořit ve složce % TEMP %. Může existovat instancí se neodstraní některé dočasné soubory z důvodu problémy načasování. Například, pokud jsou soubory používá aktuální domény aplikace nebo pomocí ladicího programu, finalizační metodu <xref:System.CodeDom.Compiler.TempFileCollection> objekt nebude možné je odstranit.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> Vlastnost lze použít pro další čištění. abyste měli jistotu, že všechny dočasné soubory byly odebrány z klienta.  
  
### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>Podpora pro elementu xsl: Output elementu a XmlWriter  
 <xref:System.Xml.Xsl.XslTransform> Třídy Ignorovat `xsl:output` nastavení při výstupu transformace byla odeslána do <xref:System.Xml.XmlWriter> objektu. <xref:System.Xml.Xsl.XslCompiledTransform> Třída má <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> vlastnost, která vrátí <xref:System.Xml.XmlWriterSettings> objekt obsahující informace o výstupu odvozený od `xsl:output` elementu šablony stylů. <xref:System.Xml.XmlWriterSettings> Objektu se používá k vytvoření <xref:System.Xml.XmlWriter> objekt se správným nastavením, které mohou být předány <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody. Následující kód jazyka C# ukazuje toto chování:  
  
```  
// Create the XslTransform object and load the style sheet.  
XslCompiledTransform xslt = new XslCompiledTransform();  
xslt.Load(stylesheet);  
  
// Load the file to transform.  
XPathDocument doc = new XPathDocument(filename);  
  
// Create the writer.  
XmlWriter writer = XmlWriter.Create(Console.Out, xslt.OutputSettings);  
  
// Transform the file and send the output to the console.  
xslt.Transform(doc, writer);  
writer.Close();  
```  
  
### <a name="debug-option"></a>Debug – možnost  
 <xref:System.Xml.Xsl.XslCompiledTransform> Třída může generovat ladicí informace, které umožňuje provádět ladění stylů se Microsoft Visual Studio Debugger. Další informace naleznete v tématu <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.  
  
## <a name="behavioral-differences"></a>Behaviorální rozdíly  
  
### <a name="transforming-to-an-xmlreader"></a>Transformace do třídy XmlReader  
 <xref:System.Xml.Xsl.XslTransform> Třída má několik přetížení transformace, které vracejí výsledky transformace jako <xref:System.Xml.XmlReader> objektu. Tato přetížení slouží k načtení výsledků transformace do reprezentaci v paměti (například <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument>) bez dalších nákladů na režii serializace a deserializace výsledného kódu XML stromu. Následující kód jazyka C# ukazuje, jak načíst výsledky transformace do <xref:System.Xml.XmlDocument> objektu.  
  
```  
// Load the style sheet  
XslTransform xslt = new XslTransform();  
xslt.Load("MyStylesheet.xsl");  
  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
doc.Load(xslt.Transform(input, (XsltArgumentList)null));  
```  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Třída nepodporuje transformaci na <xref:System.Xml.XmlReader> objektu. Ale můžete udělat něco podobného podle pomocí <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> metodu pro načtení výsledný XML stromu přímo z <xref:System.Xml.XmlWriter>. Následující kód jazyka C# ukazuje, jak provést stejný úkol pomocí <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
```  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {  
    xslt.Transform(input, (XsltArgumentList)null, writer);  
}  
```  
  
### <a name="discretionary-behavior"></a>Volitelné chování  
 Verze 1.0 doporučení W3C transformace XSL (XSLT) zahrnuje oblasti, ve kterých může implementaci zprostředkovatele rozhodování o způsobu zpracování situaci. Tyto oblasti jsou považovány za volitelného chování. Existuje několik oblastí kde <xref:System.Xml.Xsl.XslCompiledTransform> chová jinak než <xref:System.Xml.Xsl.XslTransform> třídy. Další informace najdete v tématu [obnovitelné chyby XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).  
  
### <a name="extension-objects-and-script-functions"></a>Rozšíření objektů a funkcí skriptu  
 <xref:System.Xml.Xsl.XslCompiledTransform> přináší například tato dvě nová omezení týkající se použití funkce skriptu:  
  
-   Výrazy XPath může být volána pouze veřejné metody.  
  
-   Přetížení se liší od sebe navzájem na základě počtu argumentů. Pokud více než jednomu přetížení má stejný počet argumentů, bude vyvolána výjimka.  
  
 V <xref:System.Xml.Xsl.XslCompiledTransform>vazbu (metoda vyhledávání názvu) do funkce skriptu dochází v době kompilace a šablony stylů, které ve spolupráci s XslTranform mohou způsobit výjimku, pokud jsou načtené <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> podporuje s `msxsl:using` a `msxsl:assembly` podřízených elementů v rámci `msxsl:script` elementu. `msxsl:using` a `msxsl:assembly` elementy se používají k deklarování další obory názvů a sestavení pro použití v bloku skriptu. Zobrazit [bloky skriptu s použitím msxsl: script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) Další informace.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> zakazuje rozšíření objekty, které mají více přetížení se stejným číslem argumenty.  
  
### <a name="msxml-functions"></a>MSXML funkce  
 Podpora pro další MSXML funkce byly přidány do <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Následující seznam popisuje nové nebo vylepšené funkce:  
  
-   msxsl:node-nastavit: <xref:System.Xml.Xsl.XslTransform> vyžaduje argument [funkce sada uzlů](https://msdn.microsoft.com/library/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7) funkci fragment stromu výsledek. <xref:System.Xml.Xsl.XslCompiledTransform> Třída nemá tento požadavek.  
  
-   msxsl:Version: Tato funkce není podporována v <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
-   Funkcí rozšíření XPath: [ms:string-compare – funkce](https://msdn.microsoft.com/library/20616b82-9e27-444c-b714-4f1e09b73aee), [ms:utc funkce](https://msdn.microsoft.com/library/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f), [MS: namespace-uri funkce](https://msdn.microsoft.com/library/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7), [ms:local – název funkce](https://msdn.microsoft.com/library/10ed60a1-17a9-4d74-8b98-7940ac97c0b5), [ms:number – funkce](https://msdn.microsoft.com/library/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954), [ms:format-datum funkce](https://msdn.microsoft.com/library/51f35609-89a9-4098-a166-88bf01300bf5), a [ms:format – čas funkce](https://msdn.microsoft.com/library/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5) funkce jsou nyní podporovány.  
  
-   Schéma souvisejících funkcí rozšíření XPath: tyto funkce nepodporuje nativně podle <xref:System.Xml.Xsl.XslCompiledTransform>. Ale že je možné implementovat jako funkcí rozšíření.  
  
## <a name="see-also"></a>Viz také:

- [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [Používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
