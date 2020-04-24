---
title: Nástroje definice schématu XML (Xsd.exe)
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: 6ec99e77db4215184547ea2bbbe0d1ff8ad3c286
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389776"
---
# <a name="xml-schema-definition-tool-xsdexe"></a>Nástroje definice schématu XML (Xsd.exe)

Nástroj pro definici schématu XML (Xsd.exe) generuje schématu XML nebo běžné language runtime třídy z XDR, XML a XSD souborů nebo ze třídy v sestavení modulu runtime.

Nástroj pro definici schématu XML (XSD. exe) obvykle najdete v následující cestě: \
_C:\\Program Files (x86)\\Microsoft SDK\\Windows\\{Version}\\bin\\netfx {Version} Tools\\_

## <a name="syntax"></a>Syntaxe

Spusťte nástroj z příkazového řádku.

```console
xsd file.xdr [-outputdir:directory][/parameters:file.xml]
xsd file.xml [-outputdir:directory] [/parameters:file.xml]
xsd file.xsd {/classes | /dataset} [/element:element]
             [/enableLinqDataSet] [/language:language]
                          [/namespace:namespace] [-outputdir:directory] [URI:uri]
                          [/parameters:file.xml]
xsd {file.dll | file.exe} [-outputdir:directory] [/type:typename [...]][/parameters:file.xml]
```
  
> [!TIP]
> Aby .NET Framework nástroje správně fungovaly, musíte správně nastavit proměnné `Path`prostředí `Include`, a `Lib` . Nastavte tyto proměnné prostředí spuštěním SDKVars. bat, který je umístěný v adresáři \<SDK> \v2.0\Bin Directory. SDKVars.bat je třeba spustit v každém příkazovém prostředí.

## <a name="argument"></a>Argument

|Argument|Popis|
|--------------|-----------------|
|*soubor. Extension*|Určuje vstupní soubor převést. Přípona musí být zadána jako jedna z následujících:. XDR,. XML,. xsd,. dll nebo. exe.<br /><br /> Pokud zadáte soubor schématu XDR (soubory s příponou .xdr), převede Xsd.exe schéma XDR schéma XSD. Výstupní soubor má stejný název jako schéma XDR, ale s příponou XSD.<br /><br /> Pokud zadáte soubor XML (soubory s příponou XML), Xsd.exe odvodí schéma z dat v souboru a vytvoří schéma XSD. Výstupní soubor má stejný název jako soubor XML, ale s příponou XSD.<br /><br /> Pokud zadáte soubor schématu XML (soubory s příponou XSD), vygeneruje Xsd.exe zdrojový kód pro objekty modulu runtime, které odpovídají schématu XML.<br /><br /> Pokud zadáte soubor sestavení modulu runtime (s příponou .exe nebo .dll), vygeneruje Xsd.exe schémata pro jeden nebo více typů v tomto sestavení. Můžete použít `/type` můžete určit typy, pro které se mají vygenerovat schémata. Výstup schémata jsou s názvem schema0.xsd, schema1.xsd a tak dále. XSD.exe vytváří více schémat pouze v případě, že daných typů zadejte obor názvů pomocí `XMLRoot` vlastního atributu.|

## <a name="general-options"></a>Obecné možnosti

|Možnost|Popis|
|------------|-----------------|
|**/h\[ELP\]**|Zobrazí syntaxi příkazu a možnosti nástroje.|
|**/o\[utputdir\]:**_adresář_|Určuje výstupní soubory v adresáři. Tento argument může být pouze jednou. Výchozí je aktuální adresář.|
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|
|**/p\[arameters\]:**_File. XML_|Možnosti pro různé režimy operace čtení ze souboru zadaného .xml. Krátký tvar je `/p:`. Další informace najdete v části [poznámky](#remarks) .|

## <a name="xsd-file-options"></a>Možnosti souboru XSD
 Je třeba zadat pouze jeden z následujících možností pro soubory XSD.

|Možnost|Popis|
|------------|-----------------|
|**/c\[lasses\]**|Vytvoří třídy, které odpovídají zadaným schématu. Chcete-li číst data XML do objektu, použijte <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> metodu.|
|**/d\[ataset\]**|Vygeneruje třídu odvozenou z <xref:System.Data.DataSet> , který odpovídá zadané schéma. Chcete-li číst data XML do odvozené třídy, použijte <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> metodu.|

 Můžete také určit některý z následujících možností pro soubory XSD.

|Možnost|Popis|
|------------|-----------------|
|**/e\[lementovat\]:**_element_|Určuje element ve schématu pro generování kódu pro. Ve výchozím nastavení jsou zadány všechny elementy. Tento parametr lze zadat více než jednou.|
|**/enableDataBinding**|Implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní na všechny typy generovaného povolit datové vazby. Krátký tvar je `/edb`.|
|**/enableLinqDataSet**|(Krátký tvar: `/eld`.) Určuje, že vygenerovaná datová sada může být dotazována pomocí LINQ to DataSet. Tato možnost se používá, pokud je také zadán parametr /dataset. Další informace najdete v tématu [LINQ to DataSet Overview](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) a [dotazování na typové datové sady](../../../docs/framework/data/adonet/querying-typed-datasets.md). Obecné informace o použití LINQ naleznete v tématu [Language-Integrated Query (LINQ) – C#](../../csharp/programming-guide/concepts/linq/index.md) nebo [Language-INTEGRATED Query (linq)-Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).|
|**/f\[ields\]**|Generuje polí místo vlastností. Ve výchozím nastavení jsou generovány vlastnosti.|
|**/l\[azyk\]:**_Language_|Určuje programovací jazyk, který chcete použít. Vybrat z `CS` (C#, který je ve výchozím nastavení), `VB` (Visual Basic), `JS` (JScript), nebo `VJS` (Visual J#). Můžete také zadat plně kvalifikovaný název třídy implementující<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>|
|**/n\[amespace\]:**_Namespace_|Určuje runtime obor názvů pro generovaný typy. Výchozí obor názvů je `Schemas`.|
|**/nologo**|Potlačí hlavičky.|
|**/Order**|Generuje explicitní pořadí identifikátory pro všechny členy částic.|
|**/o\[UT\]:**_Directory_|Určuje výstupní adresář pro soubory v. Výchozí je aktuální adresář.|
|**/u\[rezervované\]instance:**_URI_|Určuje identifikátor URI pro elementy ve schématu pro generování kódu pro. Tento identifikátor URI, pokud je k dispozici, se vztahuje na všechny prvky určené s `/element` možnost.|

## <a name="dll-and-exe-file-options"></a>Knihovna DLL a EXE soubor možnosti

|Možnost|Popis|
|------------|-----------------|
|**/t\[typ\]:**_TypeName_|Určuje název typu vytvořit schéma pro. Můžete zadat více argumentů typu. Pokud *TypeName* neurčuje obor názvů, XSD. exe odpovídá všem typům v sestavení se zadaným typem. Pokud *TypeName* určuje obor názvů, bude porovnán pouze tento typ. Pokud *TypeName* končí znakem hvězdičky (\*), nástroj porovná všechny typy, které začínají řetězcem, který \*se nachází před. V případě vynechání `/type` možnost, Xsd.exe generuje schémata pro všechny typy v sestavení.|

## <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny operace, že provede Xsd.exe.

| | |
|------------|-----------------|
|XDR k XSD|Generuje schématu XML ze souboru XML sníženým Data schématu. XDR je ve formátu early založený na jazyce XML schématu.|
|XML na XSD|Generuje schématu XML ze souboru XML.|
|XSD sadu dat|Generuje modul common language runtime <xref:System.Data.DataSet> třídy ze souboru schématu XSD. Generované třídy poskytují bohatý objektový model pro běžné data XML.|
|XSD do tříd|Generuje runtime třídy ze souboru schématu XSD. Generované třídy lze použít ve spojení s <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> ke čtení a zápisu kód XML, který následuje schéma.|
|Třídy, které mají XSD| Generuje schématu XML z typ nebo typy v sestavení soubor za běhu. Generované schéma definuje formát XML, který používá <xref:System.Xml.Serialization.XmlSerializer>.|

 XSD.exe umožňuje pracovat s schémat XML, které následují definici schématu XML (XSD) jazyk navrhovaná World Wide Web Consortium (W3C). Další informace o návrhu definice schématu XML nebo standardu XML naleznete v tématu <https://w3.org>.

## <a name="setting-options-with-an-xml-file"></a>Nastavení možností pomocí souboru XML

Pomocí `/parameters` přepínače můžete zadat jeden soubor XML, který nastaví různé možnosti. Možnosti můžete nastavit, závisí na tom, jak používáte nástroj XSD.exe. Vybrat možnost generování schémat, generování kódu soubory nebo soubory s kódem, mezi které patří generování `DataSet` funkce. Můžete například nastavit `<assembly>` element na název spustitelného souboru (.exe) nebo souboru typu knihovna (DLL) při generování schématu, ale ne v případě, že generování souboru kódu. Následující kód XML ukazuje, jak lze použít `<generateSchemas>` element se zadaným spustitelného souboru:

```xml
<!-- This is in a file named GenerateSchemas.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <assembly>ConsoleApplication1.exe</assembly>
</generateSchemas>
</xsd>
```

Pokud je předchozí kód XML obsažen v souboru s názvem GenerateSchemas. XML, použijte `/parameters` přepínač zadáním následujícího příkazu na příkazovém řádku a stisknutím klávesy **ENTER**:

```console
 xsd /p:GenerateSchemas.xml
```

Na druhé straně Pokud jsou generování schéma pro jeden typ nalezen v sestavení, můžete použít následující kód XML:

```xml
<!-- This is in a file named GenerateSchemaFromType.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <type>IDItems</type>
</generateSchemas>
</xsd>
```

Ale při použití předcházející kódu, je třeba zadat také název sestavení na příkazovém řádku. Na příkazovém řádku zadejte následující příkaz (předpokládá se, že soubor XML má název GenerateSchemaFromType. XML):

```console
xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe
```

Je třeba zadat pouze jeden z následujících možností `<generateSchemas>` elementu.

|Prvek|Popis|
|-------------|-----------------|
|\<> sestavení|Určuje sestavení, které chcete vytvořit schéma z.|
|\<Zadejte>|Určuje typ v sestavení, které chcete vytvořit schéma pro nalezen.|
|\<> XML|Určuje soubor XML pro schéma pro generování.|
|\<> XDR|Určuje soubor XDR ke generování schéma pro.|

Chcete-li generovat soubor s kódem, použijte `<generateClasses>` elementu. Následující příklad generuje soubor kódu. Všimněte si, že jsou také zobrazeny dva atributy, které umožňují nastavit programovací jazyk a obor názvů generovaného souboru.

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>
</xsd>
<!-- You must supply an .xsd file when typing in the command line.-->
<!-- For example: xsd /p:genClasses mySchema.xsd -->
```

 Možnosti pro můžete nastavit `<generateClasses>` element patří následující.

|Prvek|Popis|
|-------------|-----------------|
|\<> elementu|Určuje element v souboru XSD pro generování kódu pro.|
|\<schemaImporterExtensions>|Určuje typu odvozeného z <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> třídy.|
|\<> schématu|Určuje soubor schématu XML pro generování kódu pro. Pomocí více \<> prvků schématu lze zadat více souborů schématu XML.|

V následující tabulce jsou uvedeny atributy, které lze také použít s `<generateClasses>` elementu.

|Atribut|Popis|
|---------------|-----------------|
|language|Určuje programovací jazyk, který chcete použít. Vybrat z `CS` (C#, výchozí nastavení), `VB` (Visual Basic), `JS` (JScript), nebo `VJS` (Visual J#). Můžete také zadat plně kvalifikovaný název pro třídu, která implementuje <xref:System.CodeDom.Compiler.CodeDomProvider>.|
|namespace|Určuje obor názvů pro generovaný kód. Obor názvů musí odpovídat CLR standardů (například bez mezer nebo zpětné lomítko znaků).|
|možnosti|Jedna z `none`následujících hodnot:, `properties` (generuje vlastnosti namísto veřejných polí), `order`, nebo `enableDataBinding` (viz přepínače `/order` a `/enableDataBinding` v předchozím oddílu Možnosti souboru XSD.|

 Můžete také určit, jak `DataSet` kód je generována pomocí `<generateDataSet>` elementu. Následující kód XML určuje, že generovaný kód používá `DataSet` struktury (například <xref:System.Data.DataTable> třídu) k vytvoření kódu Visual Basic pro zadaný element. Vygenerovaný struktury datová sada bude podporovat LINQ dotazů.

 ```xml
 <xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
     <generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>
     </generateDataSet>
 </xsd>
```

Možnosti pro můžete nastavit `<generateDataSet>` element patří následující.

|Prvek|Popis|
|-------------|-----------------|
|\<> schématu|Určuje soubor schématu XML pro generování kódu pro. Pomocí více \<> prvků schématu lze zadat více souborů schématu XML.|

 V následující tabulce jsou uvedeny atributy, které lze používat s `<generateDataSet>` elementu.

|Atribut|Popis|
|---------------|-----------------|
|enableLinqDataSet|Určuje, že generované datová sada může být dotázán proti pomocí jazyka LINQ k datové. Výchozí hodnota je False.|
|language|Určuje programovací jazyk, který chcete použít. Vybrat z `CS` (C#, výchozí nastavení), `VB` (Visual Basic), `JS` (JScript), nebo `VJS` (Visual J#). Můžete také zadat plně kvalifikovaný název pro třídu, která implementuje <xref:System.CodeDom.Compiler.CodeDomProvider>.|
|namespace|Určuje obor názvů pro generovaný kód. Obor názvů musí odpovídat CLR standardů (například bez mezer nebo zpětné lomítko znaků).|

 Atributy, které lze nastavit na nejvyšší úrovni `<xsd>` elementu. Tyto možnosti lze používat s některou z podřízených prvků (`<generateSchemas>`, `<generateClasses>` nebo `<generateDataSet>`). Následující kód XML generuje kód pro element s názvem "IDItems" v adresáři výstupu s názvem "MyOutputDirectory".

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>
<generateClasses>
    <element>IDItems</element>
</generateClasses>
</xsd>
```

V následující tabulce jsou uvedeny atributy, které lze také použít s `<xsd>` elementu.

|Atribut|Popis|
|---------------|-----------------|
|output|Název adresáře, kde budou umístěny vygenerovaný soubor schématu nebo kódu.|
|nologo|Potlačí hlavičky. Nastavte na `true` nebo `false`.|
|Nápověda|Zobrazí syntaxi příkazu a možnosti nástroje. Nastavte na `true` nebo `false`.|

## <a name="examples"></a>Příklady
 Následující příkaz generuje schématu XML z `myFile.xdr` a uloží jej do aktuálního adresáře.

```console
xsd myFile.xdr
```

Následující příkaz generuje schématu XML z `myFile.xml` a uloží jej do zadaného adresáře.

```console
xsd myFile.xml /outputdir:myOutputDir
```

Následující příkaz generuje sadu dat, která odpovídá určenému schématu v jazyce C# a uloží jej jako `XSDSchemaFile.cs` v aktuálním adresáři.

```console
xsd /dataset /language:CS XSDSchemaFile.xsd
```

Následující příkaz generuje schémat XML pro všechny typy v sestavení `myAssembly.dll` a ukládá je jako `schema0.xsd` v aktuálním adresáři.

```console
xsd myAssembly.dll
```

## <a name="see-also"></a>Viz také

- <xref:System.Data.DataSet>
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
- [Nástroje](../../../docs/framework/tools/index.md)
- [Výzvy příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
- [Přehled LINQ to DataSet](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [Dotazy na typové datové sady](../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [LINQ (jazykově integrovaný dotaz) (C#)](../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ (jazykově integrovaný dotaz) (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/index.md)
