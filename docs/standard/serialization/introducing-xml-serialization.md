---
title: Představení serializace XML
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
ms.openlocfilehash: b1d91306c9cc9788046d19cc5de9e4712cdaa7e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772543"
---
# <a name="introducing-xml-serialization"></a>Představení serializace XML

Serializace je proces převodu objektu do formuláře, který lze snadno přenést. Například může serializovat objekt a přenosu je prostřednictvím Internetu pomocí protokolu HTTP mezi klientem a serverem. Na druhém konci rekonstruuje deserializace objektu z datového proudu.

 Serializace XML serializuje pouze veřejné pole a hodnoty vlastností objektu do datový proud XML. Serializace XML neobsahuje informace o typu. Pokud máte například **knihy** objekt, který existuje v **knihovny** obor názvů, neexistuje žádná záruka, že je deserializovat do objektu stejného typu.

> [!NOTE]
> Serializace XML nepřevádět metody, indexery, soukromé pole nebo vlastnosti jen pro čtení (s výjimkou kolekce jen pro čtení). K serializaci všechny objektu polí a vlastností, veřejné a soukromé, použijte <xref:System.Runtime.Serialization.DataContractSerializer> namísto serializace XML.

 Centrální třída v serializaci XML je <xref:System.Xml.Serialization.XmlSerializer> třídy a nejdůležitějších metod této třídy jsou **serializace** a **Deserialize** metody. <xref:System.Xml.Serialization.XmlSerializer> Vytváří soubory jazyka C# a jejich kompiluje do soubory DLL a provést serializace. V rozhraní .NET Framework 2.0 [nástroj XML Serializer Generator (Sgen.exe)](xml-serializer-generator-tool-sgen-exe.md) je určena ke generování těchto sestavení serializace předem, chcete-li být nasazeny s vaší aplikací a zlepšit výkon při spuštění. Datový proud XML generovaných **XmlSerializer** je v souladu s World Wide Web Consortium (W3C) [schéma XML definice jazyk (XSD) 1.0 doporučení](https://www.w3.org/TR/xslt). Kromě toho jsou datové typy generovány kompatibilní s dokumentu s názvem "XML schématu část 2: Datové typy."

 Data v objekty je popsána pomocí konstrukcí programovací jazyk jako třídy, pole, vlastnosti, primitivní typy, pole a dokonce i vloženého XML ve formě **XmlElement** nebo **XmlAttribute**objekty. Máte možnost vytvořit vlastní třídy označena s atributy, nebo pomocí nástroje definici schématu XML vygenerovat třídy založen na stávajícím schématu XML.

 Pokud máte schématu XML, můžete spustit nástroj definici schématu XML k vytvoření sadu tříd, které jsou silného typu schématu a označena s atributy. Pokud instance této třídy serializován, generovaný XML dodržuje schématu XML. Za předpokladu tříd se můžete programovat proti snadno s ní manipulováno objektový model při zachování zajištěno, že generovaného kódu XML odpovídá schématu XML. Jedná se o alternativu k použití jiných tříd v rozhraní .NET Framework, jako **XmlReader** a **XmlWriter** třídy pro analýzu a zapsat datový proud XML. Další informace najdete v tématu [XML dokumenty a Data](../../../docs/standard/data/xml/index.md). Tyto třídy umožňují analyzovat jakékoli datový proud XML. Naopak použít **XmlSerializer** očekávaného datový proud XML tak, aby odpovídal známé schématu XML.

 Atributy řídí datový proud XML generovaných **XmlSerializer** třídy, což vám umožní nastavit obor názvů XML, název elementu, název atributu a tak dále datového proudu XML. Další informace o těchto atributů a způsob, jakým se řídí serializace XML, naleznete v tématu [řízení XML serializace pomocí atributů](controlling-xml-serialization-using-attributes.md). Tabulka obsahující tyto atributy, které se používají k řízení vygenerovaný kód XML, naleznete v tématu [atributy, které ovládací prvek XML serializace](attributes-that-control-xml-serialization.md).

 **XmlSerializer** třídy lze dále serializovat objekt a generovat kódovaného datový proud XML protokolu SOAP. Vygenerovaný XML dodržuje část 5 W3c dokumentu s názvem "Simple Object Access Protocol (SOAP) 1.1." Další informace o tomto procesu najdete v tématu [jak: Serializace objektu jako XML kódováním protokolu SOAP Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md). Tabulka obsahující atributy, které řídí vygenerovaný kód XML, naleznete v tématu [atributy, které ovládací prvek kódovaný SOAP serializace](attributes-that-control-encoded-soap-serialization.md).

 **XmlSerializer** třídy generuje zprávy protokolu SOAP vytvořen a předán webové služby XML. Chcete-li řídit zprávy protokolu SOAP, můžete použít atributy do třídy, vrácené hodnoty, parametry a pole nalezen v souboru XML webové služby (.asmx). Můžete použít atributy uvedené v "Atributy, aby ovládací prvek XML serializace" a "Atributy, aby ovládací prvek kódovaný SOAP serializace", protože webové služby XML lze použít buď literál nebo kódovaného protokolu SOAP stylu. Další informace o použití atributů k ovládání XML generovaných webové služby XML, naleznete v tématu [serializace XML pomocí webových služeb XML](xml-serialization-with-xml-web-services.md). Další informace o protokolu SOAP a XML webových služeb najdete v tématu [přizpůsobení formátování zprávy protokolu SOAP](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dkwy2d72(v=vs.100)).

## <a name="security-considerations-for-xmlserializer-applications"></a>Důležité informace o zabezpečení pro XmlSerializer aplikace

Při vytvoření aplikace, která používá **XmlSerializer**, je třeba si uvědomit následující položky a jejich důsledky:

- **XmlSerializer** vytvoří C# (cs), soubory a jejich kompiluje do soubory DLL v adresáři s názvem podle proměnná prostředí TEMP; s těmito knihovnami DLL dojde k serializaci.

  > [!NOTE]
  > Tyto sestavení serializace můžete předem vygenerovaných a podepsán pomocí nástroje SGen.exe. To nepomáhá serveru webové služby. Jinými slovy je pouze pro použití klienta a pro ruční serializaci.

  Kód a knihoven DLL, která jsou citlivé na škodlivý proces v době vytvoření a sestavení. Používáte-li počítači se systémem Microsoft Windows NT 4.0 nebo novější, je možné, že dvě nebo více mohou uživatelé sdílet adresář TEMP. Sdílení adresář TEMP je nebezpečné, pokud dva účty máte oprávnění různé zabezpečení a vyšší oprávnění účtu spustí aplikace pomocí **XmlSerializer**. V takovém případě může jeden uživatel porušení zabezpečení počítače nahrazením cs nebo DLL souboru, který je zkompilován. Chcete-li tento problém odstranit, vždy ujistěte se, že každý účet v počítači má vlastní profil. Ve výchozím nastavení proměnná prostředí TEMP odkazuje na jiný adresář pro každý účet.

- Pokud uživatel se zlými úmysly odešle souvislého datového proudu dat XML na webový server (útoku služby), pak bude **XmlSerializer** pokračuje ve zpracování dat, dokud počítač nedostatek na prostředky.

  Tento druh útoku se eliminují, pokud používáte počítač se systémem Internet Information Services (IIS) a je aplikace spuštěna v rámci služby IIS. Služba IIS obsahuje jako brána, který nezpracovává datových proudů delší než nastavené množství (výchozí hodnota je 4 KB). Pokud vytvoříte aplikaci, která nepoužívají služby IIS a deserializuje s **XmlSerializer**, měli byste implementovat podobně jako brána, který zabraňuje útoku služby.

- **XmlSerializer** serializuje data a spouští všechny kódu pomocí libovolného typu vzhledem k němu.

  V které škodlivý objekt představuje hrozbu dvěma způsoby. Spustí škodlivý kód nebo ji může injektovat škodlivý kód do souboru C# vytvořené **XmlSerializer**. V případě, první Pokud škodlivý objekt se pokusí spustit proceduru destruktivních zabezpečení přístupu ke kódu zabraňuje škody prováděné. V druhém případě je teoretická možnost, že škodlivý objekt může nějakého důvodu vloží kód do souboru C# vytvořené **XmlSerializer**. I když má prověřit tento problém, důkladně a takového útoku je považován za pravděpodobné, byste měli vzít preventivní opatření nikdy serializace dat s typem neznámý a nedůvěryhodný.

- Serializovaná citlivá data může být ohrožena.

  Po **XmlSerializer** má serializovat data, je možné ho uložit jako soubor XML nebo jiného úložiště dat. Pokud vaše úložiště dat je k dispozici pro procesy nebo je zobrazen v intranetu nebo Internetu, můžete data odcizení a záměrně použity. Například pokud vytvoříte aplikaci, která serializuje objednávky obsahující čísla kreditních karet, je velmi důvěrná data. K tomu nedocházelo, vždy chránit úložiště dat a proveďte kroky, které chcete zachovat privátní.

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

Další příklady serializace naleznete v tématu [příklady serializace XML](examples-of-xml-serialization.md).

## <a name="items-that-can-be-serialized"></a>Položky, které lze serializovat

Následující položky lze serializovat pomocí **XmLSerializer** třídy:

- Vlastnosti veřejné čtení a zápis a pole veřejné třídy.

- Třídy, které implementují **rozhraní ICollection** nebo **IEnumerable**.

  > [!NOTE]
  > Pouze kolekce jsou serializovaná, není veřejné vlastnosti.

- **Třída XmlElement** objekty.

- **XmlNode** objekty.

- **Datová sada** objekty.

 Další informace o serializaci nebo deserializaci objektů, naleznete v tématu [jak: Serializace objektu](how-to-serialize-an-object.md) a [jak: Deserializace objektu](how-to-deserialize-an-object.md).

## <a name="advantages-of-using-xml-serialization"></a>Výhody použití serializace XML

**XmlSerializer** třídy získáte kompletní a flexibilní kontrolu při serializaci objektu jako XML. Pokud vytváříte webové služby XML, můžete použít atributy, které řídí serializace za účelem třídy a členy zajistit, že výstup kódu XML odpovídá určité schéma.

Například **XmlSerializer** vám umožní:

- Zadejte, zda pole nebo vlastnost by měla být zakódován jako atribut nebo element.

- Zadejte obor názvů XML používat.

- Zadejte název elementu nebo atributu, pokud je název pole nebo vlastnost nevhodný.

Další výhodou serializace XML je, zda máte bez omezení na aplikací, které vytvoříte, jako datový proud XML, který je generován odpovídá dané schéma. Představte si schématu, který slouží k popisu knihy. Nabízí nadpis, Autor, vydavatel a ISBN čísla elementu. Můžete vyvíjet aplikace, která zpracovává data XML v jakékoli požadovaným způsobem, například jako pořadí adresáře nebo jako inventáře knihy. V obou případech jediným požadavkem je, že datový proud XML odpovídá zadané schéma jazyka (XSD) definice schématu XML.

## <a name="xml-serialization-considerations"></a>Důležité informace o serializaci XML

Následující by měly být považovány za při použití **XmlSerializer** třídy:

- Nástroj Sgen.exe je výslovně určena ke generování sestavení serializace pro optimální výkon.

- Serializovaná data obsahuje vlastní data a strukturu vaší třídy. Informace o typu identitu a sestavení nejsou zahrnuty.

- Pouze veřejné vlastnosti a pole lze serializovat. Vlastnosti musí mít veřejnou přistupující objekty (get a set metod). Pokud musí serializovat neveřejným dat, použijte <xref:System.Runtime.Serialization.DataContractSerializer> třídy a serializace XML.

- Třída musí mít konstruktor bylo serializováno modulem **XmlSerializer**.

- Metody nelze serializovat.

- **XmlSerializer** může zpracovat třídy, které implementují **IEnumerable** nebo **rozhraní ICollection** odlišně, pokud takto splňují určité požadavky.

  Třídu, která implementuje **IEnumerable** musí implementovat veřejné **přidat** metodu, která přijímá jeden parametr. **Přidat** parametr metody musí být konzistentní (polymorfní) s typem vrácená z **IEnumerator.Current** vlastnost vrácená z **GetEnumerator** Metoda.

  Třídu, která implementuje **rozhraní ICollection** kromě **IEnumerable** (například **CollectionBase**) musí mít veřejnou **položky** indexovat vlastnosti (indexer v jazyce C#), který přebírá celé číslo a musí mít veřejnou **počet** vlastnost typu **celé číslo**. Parametr předána **přidat** metoda musí být stejného typu, který vrátil **položky** vlastnost nebo jedna z daného typu základny.

  Pro třídy, které implementují **rozhraní ICollection**, hodnoty, které mají být serializován jsou načteny z indexované **položky** vlastnost volat **GetEnumerator**. Také veřejné polí a vlastností nejsou serializován, s výjimkou veřejné pole, která vrací jiné třídy kolekce (ten, který implementuje **rozhraní ICollection**). Příklad najdete v tématu [příklady serializace XML](examples-of-xml-serialization.md).

## <a name="xsd-data-type-mapping"></a>Mapování typů dat XSD

W3C dokumentu s názvem [XML schématu část 2: Datové typy](https://www.w3.org/TR/xmlschema-2/) určuje jednoduché datové typy, které jsou povoleny ve schématu schématu XML definice jazyk (XSD). Pro mnoho z nich (například **int** a **desítkové**), neexistuje odpovídající typ dat v rozhraní .NET Framework. Nicméně některé typy dat XML nemají odpovídající typ dat v rozhraní .NET Framework (třeba **NMTOKEN** datový typ). V takových případech, pokud použijete nástroj definici schématu XML ([nástroj definici schématu XML (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)) ke generování třídy z schématu, odpovídajícího atributu se použije na člena typu řetězec a jeho **datovýtyp** je nastavena na název datového typu XML. Například pokud schématu obsahuje element s názvem "MyToken" s datovým typem XML **NMTOKEN**, generovaná třída může obsahovat člena, jak je znázorněno v následujícím příkladu.

```vb
<XmlElement(DataType:="NMTOKEN")> _
Public MyToken As String
```

```csharp
[XmlElement(DataType = "NMTOKEN")]
public string MyToken;
```

Podobně, pokud vytváříte třídu, která musí odpovídat na konkrétní schématu XML (XSD), můžete byste použít příslušný atribut a nastavit jeho **datový typ** vlastnost má požadovaná data XML zadejte název.

Úplný seznam mapování typů, najdete v článku **datový typ** vlastnosti pro všechny následující třídy atributu:

- <xref:System.Xml.Serialization.SoapAttributeAttribute>

- <xref:System.Xml.Serialization.SoapElementAttribute>

- <xref:System.Xml.Serialization.XmlArrayItemAttribute>

- <xref:System.Xml.Serialization.XmlAttributeAttribute>

- <xref:System.Xml.Serialization.XmlElementAttribute>

- <xref:System.Xml.Serialization.XmlRootAttribute>

## <a name="see-also"></a>Viz také:

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
