---
title: Podrobnosti o serializaci XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, about XML serialization
- ICollection interface, serializing
- XmlSerializer class, serializing
- serialization, about serialization
- DataSet class, serializing
- XML Schema, serializing
ms.assetid: 8c63200d-db63-4a03-a93d-21641623df62
ms.openlocfilehash: d644e80cbf5ac17fca4df039d915c847a1936217
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588458"
---
# <a name="xml-serialization"></a>serializace XML

Serializace je proces převodu objektu do formuláře, který lze snadno přenést. Například může serializovat objekt a přenosu je prostřednictvím Internetu pomocí protokolu HTTP mezi klientem a serverem. Na druhém konci rekonstruuje deserializace objektu z datového proudu.

 Serializace XML serializuje pouze veřejné pole a hodnoty vlastností objektu do datový proud XML. Serializace XML neobsahuje informace o typu. Například pokud máte **Book** objekt, který existuje v oboru názvů **knihovny,** neexistuje žádná záruka, že je deserializován do objektu stejného typu.

> [!NOTE]
> Serializace XML nepřevádět metody, indexery, soukromé pole nebo vlastnosti jen pro čtení (s výjimkou kolekce jen pro čtení). K serializaci všechny objektu polí a vlastností, veřejné a soukromé, použijte <xref:System.Runtime.Serialization.DataContractSerializer> namísto serializace XML.

 Centrální třída v serializaci <xref:System.Xml.Serialization.XmlSerializer> XML je třída a nejdůležitější metody v této třídě jsou **Serializovat** a **Deserializovat** metody. <xref:System.Xml.Serialization.XmlSerializer> Vytváří soubory jazyka C# a jejich kompiluje do soubory DLL a provést serializace. V rozhraní .NET Framework 2.0 je [nástroj generátor serializátoru XML (Sgen.exe)](xml-serializer-generator-tool-sgen-exe.md) navržen tak, aby předem generoval tato sestavení serializace, která mají být nasazena s vaší aplikací a zlepšit výkon při spuštění. Datový proud XML generovaný **xmlserializátorem** je kompatibilní s [doporučením 1.0 jazyka jazyka xml (Schema) konsorcia Xml (World](https://www.w3.org/TR/xslt)Wide Web Consortium) . Kromě toho jsou typy dat, které jsou generovány kompatibilní s dokumentu s názvem "část schématu XML 2: datové typy."

 Data v objektech jsou popsána pomocí konstrukcí programovacího jazyka, jako jsou třídy, pole, vlastnosti, primitivní typy, pole a dokonce i vložený XML ve formě objektů **XmlElement** nebo **XmlAttribute.** Máte možnost vytvořit vlastní třídy označena s atributy, nebo pomocí nástroje definici schématu XML vygenerovat třídy založen na stávajícím schématu XML.

 Pokud máte schématu XML, můžete spustit nástroj definici schématu XML k vytvoření sadu tříd, které jsou silného typu schématu a označena s atributy. Pokud instance této třídy serializován, generovaný XML dodržuje schématu XML. Za předpokladu tříd se můžete programovat proti snadno s ní manipulováno objektový model při zachování zajištěno, že generovaného kódu XML odpovídá schématu XML. Toto je alternativa k použití jiných tříd v rozhraní .NET Framework, jako jsou **xmlreader** a **xmlwriter** třídy, analyzovat a zapisovat datový proud XML. Další informace naleznete v tématu [Dokumenty xml a data](../../../docs/standard/data/xml/index.md). Tyto třídy umožňují analyzovat jakékoli datový proud XML. Naproti tomu použijte **xmlserializer,** pokud se očekává, že datový proud XML odpovídá známému schématu XML.

 Atributy řídí datový proud XML generovaný třídou **XmlSerializer,** což umožňuje nastavit obor názvů XML, název prvku, název atributu a tak dále datového proudu XML. Další informace o těchto atributech a způsobu jejich řízení serializace XML naleznete [v tématu Řízení serializace XML pomocí atributů](controlling-xml-serialization-using-attributes.md). Tabulka těchto atributů, které se používají k řízení generovaného xml, naleznete v [tématu Atributy, které řídí serializaci XML](attributes-that-control-xml-serialization.md).

 Třída **XmlSerializer** může dále serializovat objekt a generovat kódovaný datový proud SOAP XML. Vygenerovaný XML dodržuje část 5 W3c dokumentu s názvem "Simple Object Access Protocol (SOAP) 1.1." Další informace o tomto procesu naleznete v [tématu How to: Serialize objektu jako datového proudu XML s kódováním SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md). Tabulka atributů, které řídí generovaný kód XML, naleznete v [tématu Atributy, které řídí kódovanou serializaci SOAP](attributes-that-control-encoded-soap-serialization.md).

 Třída **XmlSerializer** generuje zprávy SOAP vytvořené a předávané webovým službám XML. Chcete-li řídit zprávy protokolu SOAP, můžete použít atributy do třídy, vrácené hodnoty, parametry a pole nalezen v souboru XML webové služby (.asmx). Můžete použít atributy uvedené v "Atributy, aby ovládací prvek XML serializace" a "Atributy, aby ovládací prvek kódovaný SOAP serializace", protože webové služby XML lze použít buď literál nebo kódovaného protokolu SOAP stylu. Další informace o použití atributů k řízení xml generovaného webovou službou XML naleznete [v tématu Serializace XML pomocí webových služeb XML](xml-serialization-with-xml-web-services.md). Další informace o webových službách SOAP a XML naleznete v [tématu Přizpůsobení formátování zpráv SOAP](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dkwy2d72(v=vs.100)).

## <a name="security-considerations-for-xmlserializer-applications"></a>Důležité informace o zabezpečení pro XmlSerializer aplikace

Při vytváření aplikace, která používá **XmlSerializer**, uvědomte si následující položky a jejich důsledky:

- **XmlSerializer** vytvoří soubory Jazyka C# (.cs) a zkompiluje je do souborů DLL v adresáři pojmenovaném proměnnou prostředí TEMP; serializace probíhá s těmito knihovnami DLL.

  > [!NOTE]
  > Tyto sestavení serializace můžete předem vygenerovaných a podepsán pomocí nástroje SGen.exe. To nepomáhá serveru webové služby. Jinými slovy je pouze pro použití klienta a pro ruční serializaci.

  Kód a knihoven DLL, která jsou citlivé na škodlivý proces v době vytvoření a sestavení. Používáte-li počítači se systémem Microsoft Windows NT 4.0 nebo novější, je možné, že dvě nebo více mohou uživatelé sdílet adresář TEMP. Sdílení adresáře TEMP je nebezpečné, pokud mají dva účty různá oprávnění zabezpečení a účet s vyššími oprávněními spouští aplikaci pomocí **xmlserializeru**. V takovém případě může jeden uživatel narušit zabezpečení počítače nahrazením kompilovaného souboru .cs nebo DLL. Chcete-li tento problém odstranit, vždy ujistěte se, že každý účet v počítači má vlastní profil. Ve výchozím nastavení proměnná prostředí TEMP odkazuje na jiný adresář pro každý účet.

- Pokud uživatel se zlými úmysly odešle nepřetržitý datový proud dat XML na webový server (útok odmítnutí služby), bude **xmlserializer** pokračovat ve zpracování dat, dokud počítač nebude mít nedostatek prostředků.

  Tento druh útoku se eliminují, pokud používáte počítač se systémem Internet Information Services (IIS) a je aplikace spuštěna v rámci služby IIS. Služba IIS obsahuje jako brána, který nezpracovává datových proudů delší než nastavené množství (výchozí hodnota je 4 KB). Pokud vytvoříte aplikaci, která nepoužívá službu IIS a reserializuje s **XmlSerializer**, měli byste implementovat podobnou bránu, která zabraňuje útoku odmítnutí služby.

- **XmlSerializer** serializuje data a spouští libovolný kód pomocí libovolného typu, který je mu dán.

  V které škodlivý objekt představuje hrozbu dvěma způsoby. To by mohlo spustit škodlivý kód nebo by to mohlo vložit škodlivý kód do souboru C# vytvořené **XmlSerializer**. V případě, první Pokud škodlivý objekt se pokusí spustit proceduru destruktivních zabezpečení přístupu ke kódu zabraňuje škody prováděné. V druhém případě existuje teoretická možnost, že škodlivý objekt může nějakým způsobem vložit kód do souboru C# vytvořeného **xmlserializer**. I když má prověřit tento problém, důkladně a takového útoku je považován za pravděpodobné, byste měli vzít preventivní opatření nikdy serializace dat s typem neznámý a nedůvěryhodný.

- Serializovaná citlivá data může být ohrožena.

  Po **Serializace XmlSerializer** ukládají data, mohou být uloženy jako soubor XML nebo jiné úložiště dat. Pokud vaše úložiště dat je k dispozici pro procesy nebo je zobrazen v intranetu nebo Internetu, můžete data odcizení a záměrně použity. Například pokud vytvoříte aplikaci, která serializuje objednávky obsahující čísla kreditních karet, je velmi důvěrná data. K tomu nedocházelo, vždy chránit úložiště dat a proveďte kroky, které chcete zachovat privátní.

## <a name="serialization-of-a-simple-class"></a>Serializace jednoduchou třídu

Následující příklad kódu ukazuje základní třídu s polem veřejné.

```vb
Public Class OrderForm
    Public OrderDate As DateTime
End Class
```

```csharp
public class OrderForm
{
    public DateTime OrderDate;
}
```

Pokud je serializována instance této třídy, může vypadat takto.

```xml
<OrderForm>
    <OrderDate>12/12/01</OrderDate>
</OrderForm>
```

Další příklady serializace naleznete v [tématu Příklady serializace XML](examples-of-xml-serialization.md).

## <a name="items-that-can-be-serialized"></a>Položky, které lze serializovat

Následující položky lze serializovat pomocí třídy **XmLSerializer:**

- Vlastnosti veřejné čtení a zápis a pole veřejné třídy.

- Třídy, které **implementují ICollection** nebo **IEnumerable**.

  > [!NOTE]
  > Pouze kolekce jsou serializovaná, není veřejné vlastnosti.

- **XmlElement** objekty.

- **Objekty XmlNode.**

- **DataSet** objekty.

 Další informace o serializaci nebo deserializaci objektů naleznete v [tématu How to: Serialize objektu](how-to-serialize-an-object.md) a [How to: Deserialize a Object](how-to-deserialize-an-object.md).

## <a name="advantages-of-using-xml-serialization"></a>Výhody použití serializace XML

Třída **XmlSerializer** poskytuje úplné a flexibilní řízení při serializaci objektu jako XML. Pokud vytváříte webové služby XML, můžete použít atributy, které řídí serializace za účelem třídy a členy zajistit, že výstup kódu XML odpovídá určité schéma.

**Například XmlSerializer** umožňuje:

- Zadejte, zda pole nebo vlastnost by měla být zakódován jako atribut nebo element.

- Zadejte obor názvů XML používat.

- Zadejte název elementu nebo atributu, pokud je název pole nebo vlastnost nevhodný.

Další výhodou serializace XML je, zda máte bez omezení na aplikací, které vytvoříte, jako datový proud XML, který je generován odpovídá dané schéma. Představte si schématu, který slouží k popisu knihy. Nabízí nadpis, Autor, vydavatel a ISBN čísla elementu. Můžete vyvíjet aplikace, která zpracovává data XML v jakékoli požadovaným způsobem, například jako pořadí adresáře nebo jako inventáře knihy. V obou případech jediným požadavkem je, že datový proud XML odpovídá zadané schéma jazyka (XSD) definice schématu XML.

## <a name="xml-serialization-considerations"></a>Důležité informace o serializaci XML

Při použití třídy **XmlSerializer** je třeba vzít v úvahu následující:

- Nástroj Sgen.exe je výslovně určena ke generování sestavení serializace pro optimální výkon.

- Serializovaná data obsahuje vlastní data a strukturu vaší třídy. Informace o typu identitu a sestavení nejsou zahrnuty.

- Pouze veřejné vlastnosti a pole lze serializovat. Vlastnosti musí mít veřejnou přistupující objekty (get a set metod). Pokud musí serializovat neveřejným dat, použijte <xref:System.Runtime.Serialization.DataContractSerializer> třídy a serializace XML.

- Třída musí mít konstruktor bez parametrů, který má být serializován **xmlserializátorem**.

- Metody nelze serializovat.

- **XmlSerializer** může zpracovat třídy, které implementují **IEnumerable** nebo **ICollection** odlišně, pokud splňují určité požadavky, takto.

  Třída, která implementuje **IEnumerable** musí implementovat veřejnou **Metodu Add,** která přebírá jeden parametr. Parametr **Add** metody musí být konzistentní (polymorfní) s typem vráceným z **IEnumerator.Current** vlastnost vrácena z Metody **GetEnumerator.**

  Třída, která implementuje **ICollection** kromě **IEnumerable** (například **CollectionBase**) musí mít veřejnou **položku** indexované vlastnosti (indexer v C#), který trvá celé číslo a musí mít veřejné **Count** vlastnost typu **celé číslo**. Parametr předaný metodě **Add** musí být stejného typu jako parametr vrácený z vlastnosti **Item** nebo jeden ze základů tohoto typu.

  Pro třídy, které implementují **ICollection**, hodnoty, které mají být serializovány jsou načteny z indexované **Item** vlastnost spíše než voláním **GetEnumerator**. Také veřejná pole a vlastnosti nejsou serializovány, s výjimkou veřejných polí, které vracejí jinou třídu kolekce (ten, který implementuje **ICollection).** Příklad najdete v [tématu Příklady serializace XML](examples-of-xml-serialization.md).

## <a name="xsd-data-type-mapping"></a>Mapování typů dat XSD

Dokument W3C s názvem [Schéma XML Část 2: Datové typy](https://www.w3.org/TR/xmlschema-2/) určují jednoduché datové typy, které jsou povoleny ve schématu jazyka definice schématu XML (XSD). Pro mnohé z nich (například **int** a **desítkové číslo**) je odpovídající datový typ v rozhraní .NET Framework. Některé datové typy XML však nemají odpovídající datový typ v rozhraní .NET Framework (například datový typ **NMTOKEN).** V takových případech, pokud použijete nástroj definice schématu XML ([Nástroj pro definici schématu XML (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)) ke generování tříd ze schématu, použije se na člen typu řetězec příslušný atribut a jeho vlastnost **DataType** je nastavena na název datového typu XML. Například pokud schéma obsahuje prvek s názvem "MyToken" s datovým typem XML **NMTOKEN**, generované třídy může obsahovat člen, jak je znázorněno v následujícím příkladu.

```vb
<XmlElement(DataType:="NMTOKEN")> _
Public MyToken As String
```

```csharp
[XmlElement(DataType = "NMTOKEN")]
public string MyToken;
```

Podobně pokud vytváříte třídu, která musí odpovídat určitému schématu XML (XSD), měli byste použít příslušný atribut a nastavit jeho vlastnost **DataType** na požadovaný název datového typu XML.

Úplný seznam mapování typů naleznete vlastnost **DataType** pro některou z následujících tříd atributů:

- <xref:System.Xml.Serialization.SoapAttributeAttribute>

- <xref:System.Xml.Serialization.SoapElementAttribute>

- <xref:System.Xml.Serialization.XmlArrayItemAttribute>

- <xref:System.Xml.Serialization.XmlAttributeAttribute>

- <xref:System.Xml.Serialization.XmlElementAttribute>

- <xref:System.Xml.Serialization.XmlRootAttribute>

## <a name="see-also"></a>Viz také

- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.IO.FileStream>
- [Serializace XML a SOAP](xml-and-soap-serialization.md)
- [Binární serializace](binary-serialization.md)
- [Serializace](index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [Příklady serializace XML](examples-of-xml-serialization.md)
- [Postupy: Serializace objektu](how-to-serialize-an-object.md)
- [Postupy: Deserializace objektu](how-to-deserialize-an-object.md)
