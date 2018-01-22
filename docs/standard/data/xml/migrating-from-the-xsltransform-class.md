---
title: "Migrace z XslTransform – třída"
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
ms.assetid: 9404d758-679f-4ffb-995d-3d07d817659e
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 964e2de7258f4849de01e4fbeae330d009710289
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="migrating-from-the-xsltransform-class"></a>Migrace z XslTransform – třída
Architektura XSLT byla změněna v [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)] verzi. <xref:System.Xml.Xsl.XslTransform> Třída nahradila <xref:System.Xml.Xsl.XslCompiledTransform> třídy.  
  
 Následující části popisují některé hlavní rozdíly mezi <xref:System.Xml.Xsl.XslCompiledTransform> a <xref:System.Xml.Xsl.XslTransform> třídy.  
  
## <a name="performance"></a>Výkon  
 <xref:System.Xml.Xsl.XslCompiledTransform> Třída obsahuje mnoho vylepšení výkonu. Nové procesoru XSLT zkompiluje Styl XSLT dolů common mezilehlá formátu, podobná common language runtime (CLR) nebude pro ostatní programovací jazyky. Jakmile je zkompilován šablony stylů, můžete do mezipaměti a znovu použít.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Třída také obsahuje další optimalizace, které mnohem rychlejší než <xref:System.Xml.Xsl.XslTransform> třídy.  
  
> [!NOTE]
>  I když celkový výkon <xref:System.Xml.Xsl.XslCompiledTransform> třída je lepší, než <xref:System.Xml.Xsl.XslTransform> třídy, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslCompiledTransform> třída může provádět další pomalu než <xref:System.Xml.Xsl.XslTransform.Load%2A> metodu <xref:System.Xml.Xsl.XslTransform> třída první, když je volána na transformaci. Je to proto, že soubor XSLT musí být zkompilovány, než je načten. Další informace najdete v příspěvku blogu: [XslCompiledTransform nižší než XslTransform?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="security"></a>Zabezpečení  
 Ve výchozím nastavení <xref:System.Xml.Xsl.XslCompiledTransform> třída zakáže podporu pro XSLT `document()` funkce a embedded skriptování. Tyto funkce se dá nastavit tak, že vytvoříte <xref:System.Xml.Xsl.XsltSettings> objekt, který má funkce povolena a předání do <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> metoda. Následující příklad ukazuje, jak povolit skriptování a provedení transformace XSLT.  
  
 [!code-csharp[XML_Migration#16](../../../../samples/snippets/csharp/VS_Snippets_Data/XML_Migration/CS/migration.cs#16)]
 [!code-vb[XML_Migration#16](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XML_Migration/VB/migration.vb#16)]  
  
 Další informace najdete v tématu [aspekty zabezpečení XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md).  
  
## <a name="new-features"></a>Nové funkce  
  
### <a name="temporary-files"></a>Dočasné soubory  
 Dočasné soubory jsou někdy generována během XSLT zpracování. Pokud list stylu obsahuje blocích skriptu, nebo pokud je kompilován s nastavení ladění na hodnotu true, dočasné soubory může vytvořit ve složce % TEMP %. Může existovat instance některé dočasné soubory nejsou odstraněné v důsledku problémy načasování. Například, pokud jsou soubory v používá aktuální domény aplikace nebo ladicí program finalizační metodu z <xref:System.CodeDom.Compiler.TempFileCollection> objekt nebude možné je odebrat.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.TemporaryFiles%2A> Vlastnost lze použít pro další čištění a ujistěte se, že všechny dočasné soubory byly odebrány z klienta.  
  
### <a name="support-for-the-xsloutput-element-and-xmlwriter"></a>Podpora pro elementu xsl: Output elementu a XmlWriter  
 <xref:System.Xml.Xsl.XslTransform> Třída Ignorovat `xsl:output` nastavení, když byla odeslána výstup transformace <xref:System.Xml.XmlWriter> objektu. <xref:System.Xml.Xsl.XslCompiledTransform> Třída má <xref:System.Xml.Xsl.XslCompiledTransform.OutputSettings%2A> vlastnost, která vrací <xref:System.Xml.XmlWriterSettings> objekt obsahující informace výstup odvozen od `xsl:output` element šablony stylů. <xref:System.Xml.XmlWriterSettings> Objekt se používá k vytvoření <xref:System.Xml.XmlWriter> objekt s správné nastavení, které lze předat <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoda. Následující kód C# znázorňuje toto chování:  
  
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
 <xref:System.Xml.Xsl.XslCompiledTransform> Třída může generovat ladicí informace, které umožňuje provádět ladění šablony stylů s Microsoft [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ladicí program. Další informace naleznete v tématu <xref:System.Xml.Xsl.XslCompiledTransform.%23ctor%28System.Boolean%29>.  
  
## <a name="behavioral-differences"></a>Rozdíly v chování  
  
### <a name="transforming-to-an-xmlreader"></a>Transformace na objekt XmlReader  
 <xref:System.Xml.Xsl.XslTransform> Třída má několik přetížení transformace, které vracejí výsledky transformace jako <xref:System.Xml.XmlReader> objektu. Tato přetížení slouží k načtení transformace výsledky do reprezentaci v paměti (například <xref:System.Xml.XmlDocument> nebo <xref:System.Xml.XPath.XPathDocument>) aniž by docházelo k režii serializace a deserializace výsledný soubor XML stromu. Následující kód C# ukazuje, jak načíst výsledky transformace do <xref:System.Xml.XmlDocument> objektu.  
  
```  
// Load the style sheet  
XslTransform xslt = new XslTransform();  
xslt.Load("MyStylesheet.xsl");  
  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
doc.Load(xslt.Transform(input, (XsltArgumentList)null));  
```  
  
 <xref:System.Xml.Xsl.XslCompiledTransform> Třída nepodporuje transformace na <xref:System.Xml.XmlReader> objektu. Však můžete provést něco podobného podle pomocí <xref:System.Xml.XPath.XPathNavigator.CreateNavigator%2A> metodu za účelem načtení XML výsledný strom přímo z <xref:System.Xml.XmlWriter>. Následující kód C# ukazuje, jak provádět stejné úlohy pomocí <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
```  
// Transform input document to XmlDocument for additional processing  
XmlDocument doc = new XmlDocument();  
using (XmlWriter writer = doc.CreateNavigator().AppendChild()) {  
    xslt.Transform(input, (XsltArgumentList)null, writer);  
}  
```  
  
### <a name="discretionary-behavior"></a>Volitelné chování  
 Doporučení W3C XSL transformace XSLT () verze 1.0 zahrnuje oblasti, ve kterých může implementaci zprostředkovatele rozhodování o způsobu zpracování situaci. Tyto oblasti jsou považovány za volitelné chování. Existují několik oblasti, kde <xref:System.Xml.Xsl.XslCompiledTransform> chová jinak než <xref:System.Xml.Xsl.XslTransform> – třída. Další informace najdete v tématu [obnovitelné chyby XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md).  
  
### <a name="extension-objects-and-script-functions"></a>Rozšíření objektů a funkcí skriptu  
 <xref:System.Xml.Xsl.XslCompiledTransform>zavádí dvě nové omezení použití skriptu funkcí:  
  
-   Může být volána pouze veřejné metody výrazech XPath.  
  
-   Přetížení se liší od sebe navzájem podle počet argumentů. Pokud má více než jedním přetížením stejný počet argumentů, bude vyvolána výjimka.  
  
 V <xref:System.Xml.Xsl.XslCompiledTransform>, vazbu (vyhledání názvu metoda) ke skriptu funkce nastane při kompilaci a stylů, které fungovaly s XslTranform může způsobit výjimku při načtení s <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform>podporuje s `msxsl:using` a `msxsl:assembly` podřízených elementů v rámci `msxsl:script` elementu. `msxsl:using` a `msxsl:assembly` prvky se používá k deklaraci další obory názvů a sestavení pro použití v bloku skriptu. V tématu [pomocí bloky skriptu msxsl:script](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md) Další informace.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform>zakazuje rozšíření objekty, které mají více přetížení se stejný počet argumentů.  
  
### <a name="msxml-functions"></a>Funkce MSXML  
 Podpora pro další MSXML funkce přidané <xref:System.Xml.Xsl.XslCompiledTransform> třídy. Následující seznam popisuje nové nebo vylepšené funkce:  
  
-   msxsl:node-nastavit: <xref:System.Xml.Xsl.XslTransform> vyžaduje argument [sada uzlů funkce](http://msdn.microsoft.com/library/87b6b3f4-16f4-4fa3-8103-d62a679ac2a7) funkce, která má být fragment stromu výsledek. <xref:System.Xml.Xsl.XslCompiledTransform> Třída nemá tento požadavek.  
  
-   msxsl:Version: Tato funkce není podporována v <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
-   Funkce rozšíření XPath: [ms:string-compare – funkce](http://msdn.microsoft.com/library/20616b82-9e27-444c-b714-4f1e09b73aee), [ms:utc funkce](http://msdn.microsoft.com/library/ef26fc88-84c6-4fb9-9c3b-f2f5264b864f), [ms:namespace-uri funkce](http://msdn.microsoft.com/library/91f9cabf-ab93-4dbe-9c12-e6a75214f4c7), [ms:local-název funkce](http://msdn.microsoft.com/library/10ed60a1-17a9-4d74-8b98-7940ac97c0b5), [ms:number funkce](http://msdn.microsoft.com/library/b94fc08e-1f31-4f48-b1a8-6d78c1b5d954), [ms:format-datum funkce](http://msdn.microsoft.com/library/51f35609-89a9-4098-a166-88bf01300bf5), a [ms:format-čas funkce](http://msdn.microsoft.com/library/e5c2df2d-e8fb-4a8f-bfc0-db84ea12a5d5) funkce jsou nyní podporovány.  
  
-   Schéma související funkce rozšíření XPath: tyto funkce nejsou podporovány nativně pomocí <xref:System.Xml.Xsl.XslCompiledTransform>. Však mohou být provedeny jako rozšíření funkce.  
  
## <a name="see-also"></a>Viz také  
 [Transformace XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [Používání třídy XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
