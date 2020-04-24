---
title: Podrobnosti serializace XML
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

 Serializace XML serializuje pouze veřejné pole a hodnoty vlastností objektu do datový proud XML. Serializace XML neobsahuje informace o typu. Například pokud máte objekt **knihy** , který existuje v oboru názvů **Library** , není nijak zaručeno, že je deserializován do objektu stejného typu.

> [!NOTE]
> Serializace XML nepřevádět metody, indexery, soukromé pole nebo vlastnosti jen pro čtení (s výjimkou kolekce jen pro čtení). K serializaci všechny objektu polí a vlastností, veřejné a soukromé, použijte <xref:System.Runtime.Serialization.DataContractSerializer> namísto serializace XML.

 Centrální třída v serializaci XML je <xref:System.Xml.Serialization.XmlSerializer> třída a nejdůležitější metody v této třídě jsou metody **serializace** a **deserializace** . <xref:System.Xml.Serialization.XmlSerializer> Vytváří soubory jazyka C# a jejich kompiluje do soubory DLL a provést serializace. V .NET Framework 2,0 je [XML Serializer Generator Tool (Sgen. exe)](xml-serializer-generator-tool-sgen-exe.md) navržena tak, aby se tato serializace sestavení předem generovala s vaší aplikací a zlepšila výkon při spuštění. Datový proud XML generovaný **objektem XmlSerializer** je kompatibilní s doporučením konsorcium World Wide Web (W3C) [XML Schema Definition Language (XSD) 1,0](https://www.w3.org/TR/xslt). Kromě toho jsou typy dat, které jsou generovány kompatibilní s dokumentu s názvem "část schématu XML 2: datové typy."

 Data v objektech jsou popsána pomocí konstrukcí programovacích jazyků, jako jsou třídy, pole, vlastnosti, primitivní typy, pole a dokonce i vložené XML ve formě objektů **XmlElement** nebo **XmlAttribute** . Máte možnost vytvořit vlastní třídy označena s atributy, nebo pomocí nástroje definici schématu XML vygenerovat třídy založen na stávajícím schématu XML.

 Pokud máte schématu XML, můžete spustit nástroj definici schématu XML k vytvoření sadu tříd, které jsou silného typu schématu a označena s atributy. Pokud instance této třídy serializován, generovaný XML dodržuje schématu XML. Za předpokladu tříd se můžete programovat proti snadno s ní manipulováno objektový model při zachování zajištěno, že generovaného kódu XML odpovídá schématu XML. Jedná se o alternativu k použití jiných tříd v .NET Framework, jako jsou třídy **XmlReader** a **XmlWriter** , k analýze a zápisu datového proudu XML. Další informace najdete v tématu [dokumenty a data XML](../../../docs/standard/data/xml/index.md). Tyto třídy umožňují analyzovat jakékoli datový proud XML. Naproti tomu **objekt XmlSerializer** použijte v případě, že se očekává, že datový proud XML odpovídá známému schématu XML.

 Atributy řídí datový proud XML generovaný třídou **XmlSerializer** , což umožňuje nastavit obor názvů XML, název elementu, název atributu a tak dále pro datový proud XML. Další informace o těchto atributech a o tom, jak řídí serializace XML, naleznete v tématu [řízení serializace XML pomocí atributů](controlling-xml-serialization-using-attributes.md). Tabulka pro tyto atributy, které se používají k řízení vygenerovaného kódu XML, naleznete v tématu [atributy, které řídí serializaci XML](attributes-that-control-xml-serialization.md).

 Třída **XmlSerializer** může dále serializovat objekt a generovat kódovaný datový proud SOAP XML. Vygenerovaný XML dodržuje část 5 W3c dokumentu s názvem "Simple Object Access Protocol (SOAP) 1.1." Další informace o tomto procesu naleznete v tématu [How to: serializovat objekt jako datový proud XML s kódováním SOAP](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md). Tabulku atributů, které řídí generovaný kód XML, naleznete v tématu [atributy, které řídí serializaci kódovaných SOAP](attributes-that-control-encoded-soap-serialization.md).

 Třída **XmlSerializer** generuje zprávy protokolu SOAP, které vytvořil a předal webové služby XML. Chcete-li řídit zprávy protokolu SOAP, můžete použít atributy do třídy, vrácené hodnoty, parametry a pole nalezen v souboru XML webové služby (.asmx). Můžete použít atributy uvedené v "Atributy, aby ovládací prvek XML serializace" a "Atributy, aby ovládací prvek kódovaný SOAP serializace", protože webové služby XML lze použít buď literál nebo kódovaného protokolu SOAP stylu. Další informace o použití atributů k řízení XML generovaných webovou službou XML naleznete v tématu [serializace XML s webovými službami XML](xml-serialization-with-xml-web-services.md). Další informace o webových službách SOAP a XML najdete v tématu [Přizpůsobení formátování zpráv SOAP](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dkwy2d72(v=vs.100)).

## <a name="security-considerations-for-xmlserializer-applications"></a>Důležité informace o zabezpečení pro XmlSerializer aplikace

Při vytváření aplikace, která používá **XmlSerializer**, pamatujte na následující položky a jejich důsledky:

- **XmlSerializer** vytvoří soubory C# (. cs) a zkompiluje je do souborů. dll v adresáři s názvem proměnná prostředí TEMP; s těmito knihovnami DLL dochází k serializaci.

  > [!NOTE]
  > Tyto sestavení serializace můžete předem vygenerovaných a podepsán pomocí nástroje SGen.exe. To nepomáhá serveru webové služby. Jinými slovy je pouze pro použití klienta a pro ruční serializaci.

  Kód a knihoven DLL, která jsou citlivé na škodlivý proces v době vytvoření a sestavení. Používáte-li počítači se systémem Microsoft Windows NT 4.0 nebo novější, je možné, že dvě nebo více mohou uživatelé sdílet adresář TEMP. Sdílení DOČASNÉho adresáře je nebezpečné, pokud tyto dva účty mají odlišná oprávnění zabezpečení a účet s vyšším oprávněním spouští aplikaci pomocí objektu **XmlSerializer**. V takovém případě může jeden uživatel porušení zabezpečení počítače tím, že nahradí soubor. cs nebo. dll, který je zkompilován. Chcete-li tento problém odstranit, vždy ujistěte se, že každý účet v počítači má vlastní profil. Ve výchozím nastavení proměnná prostředí TEMP odkazuje na jiný adresář pro každý účet.

- Pokud uživatel se zlými úmysly pošle souvislý proud dat XML na webový server (útok na útok DoS), pak **objekt XmlSerializer** pokračuje ve zpracování dat, dokud počítač nedosáhne nedostatku prostředků.

  Tento druh útoku se eliminují, pokud používáte počítač se systémem Internet Information Services (IIS) a je aplikace spuštěna v rámci služby IIS. Služba IIS obsahuje jako brána, který nezpracovává datových proudů delší než nastavené množství (výchozí hodnota je 4 KB). Pokud vytvoříte aplikaci, která nepoužívá službu IIS a deserializace s **objektem XmlSerializer**, měli byste implementovat podobnou bránu, která znemožňuje útok na útok DoS (Denial of Service).

- **XmlSerializer** serializace dat a spustí libovolný kód pomocí libovolného typu, který je mu předán.

  V které škodlivý objekt představuje hrozbu dvěma způsoby. Mohl by spustit škodlivý kód nebo může vložit škodlivý kód do souboru jazyka C# vytvořeného **objektem XmlSerializer**. V případě, první Pokud škodlivý objekt se pokusí spustit proceduru destruktivních zabezpečení přístupu ke kódu zabraňuje škody prováděné. V druhém případě existuje teoretická možnost, že škodlivý objekt může nějakým způsobem vkládat kód do souboru jazyka C# vytvořeného **objektem XmlSerializer**. I když má prověřit tento problém, důkladně a takového útoku je považován za pravděpodobné, byste měli vzít preventivní opatření nikdy serializace dat s typem neznámý a nedůvěryhodný.

- Serializovaná citlivá data může být ohrožena.

  Poté, co **objekt XmlSerializer** obsahuje Serializovaná data, může být uložen jako soubor XML nebo jiné úložiště dat. Pokud vaše úložiště dat je k dispozici pro procesy nebo je zobrazen v intranetu nebo Internetu, můžete data odcizení a záměrně použity. Například pokud vytvoříte aplikaci, která serializuje objednávky obsahující čísla kreditních karet, je velmi důvěrná data. K tomu nedocházelo, vždy chránit úložiště dat a proveďte kroky, které chcete zachovat privátní.

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

Další příklady serializace naleznete v tématu [Příklady serializace XML](examples-of-xml-serialization.md).

## <a name="items-that-can-be-serialized"></a>Položky, které lze serializovat

Následující položky lze serializovat pomocí třídy **XmLSerializer** :

- Vlastnosti veřejné čtení a zápis a pole veřejné třídy.

- Třídy, které implementují rozhraní **ICollection** nebo **IEnumerable**

  > [!NOTE]
  > Pouze kolekce jsou serializovaná, není veřejné vlastnosti.

- Objekty **XmlElement** .

- Objekty **XmlNode** .

- Objekty **DataSet** .

 Další informace o serializaci nebo deserializaci objektů naleznete v tématu [How to: serializovat objekt](how-to-serialize-an-object.md) a [How to: rekonstruovat Object](how-to-deserialize-an-object.md).

## <a name="advantages-of-using-xml-serialization"></a>Výhody použití serializace XML

Třída **XmlSerializer** poskytuje kompletní a flexibilní řízení při serializaci objektu jako XML. Pokud vytváříte webové služby XML, můžete použít atributy, které řídí serializace za účelem třídy a členy zajistit, že výstup kódu XML odpovídá určité schéma.

Například **XmlSerializer** umožňuje:

- Zadejte, zda pole nebo vlastnost by měla být zakódován jako atribut nebo element.

- Zadejte obor názvů XML používat.

- Zadejte název elementu nebo atributu, pokud je název pole nebo vlastnost nevhodný.

Další výhodou serializace XML je, zda máte bez omezení na aplikací, které vytvoříte, jako datový proud XML, který je generován odpovídá dané schéma. Představte si schématu, který slouží k popisu knihy. Nabízí nadpis, Autor, vydavatel a ISBN čísla elementu. Můžete vyvíjet aplikace, která zpracovává data XML v jakékoli požadovaným způsobem, například jako pořadí adresáře nebo jako inventáře knihy. V obou případech jediným požadavkem je, že datový proud XML odpovídá zadané schéma jazyka (XSD) definice schématu XML.

## <a name="xml-serialization-considerations"></a>Důležité informace o serializaci XML

Při použití třídy **XmlSerializer** je třeba zvážit následující:

- Nástroj Sgen.exe je výslovně určena ke generování sestavení serializace pro optimální výkon.

- Serializovaná data obsahuje vlastní data a strukturu vaší třídy. Informace o typu identitu a sestavení nejsou zahrnuty.

- Pouze veřejné vlastnosti a pole lze serializovat. Vlastnosti musí mít veřejnou přistupující objekty (get a set metod). Pokud musí serializovat neveřejným dat, použijte <xref:System.Runtime.Serialization.DataContractSerializer> třídy a serializace XML.

- Třída musí mít konstruktor bez parametrů, aby ji bylo možné serializovat pomocí **XmlSerializer**.

- Metody nelze serializovat.

- **XmlSerializer** může zpracovat třídy, které implementují rozhraní **IEnumerable** nebo **ICollection** odlišně, pokud splňují určité požadavky, následovně.

  Třída, která implementuje rozhraní **IEnumerable** , musí implementovat veřejnou metodu **Add** , která přijímá jeden parametr. Parametr metody **Add** musí být konzistentní (polymorfní) s typem vráceným z rozhraní **IEnumerator. Current** , který byl vrácen z metody **GetEnumerator** .

  Třída, která implementuje rozhraní **ICollection** kromě **IEnumerable** (například **CollectionBase**), musí mít indexovanou vlastnost Public **Item** (indexer v jazyce C#), která přebírá celé číslo a musí mít vlastnost veřejného **Count** typu **Integer**. Parametr předaný metodě **Add** musí být stejného typu, jako by byl vrácen z vlastnosti **Item** nebo některého z jeho základů typu.

  Pro třídy, které implementují rozhraní **ICollection**, jsou hodnoty, které mají být serializovány, načítány z vlastnosti indexované **položky** , nikoli voláním metody **GetEnumerator**. Také veřejné pole a vlastnosti nejsou serializovány, s výjimkou veřejných polí, která vracejí jinou třídu kolekce (která implementuje rozhraní **ICollection**). Příklad naleznete v tématu [Příklady serializace XML](examples-of-xml-serialization.md).

## <a name="xsd-data-type-mapping"></a>Mapování typů dat XSD

Dokument W3C s názvem [XML schématu část 2:](https://www.w3.org/TR/xmlschema-2/) datové typy určují jednoduché datové typy, které jsou povoleny ve schématu XSD (XML Schema Definition Language). Pro mnohé z těchto (například **int** a **Decimal**) existuje odpovídající datový typ v .NET Framework. Některé datové typy XML však nemají odpovídající datový typ v .NET Framework (například datový typ **NMTOKEN** ). V takových případech, pokud použijete nástroj definice schématu XML ([XSD. exe)](xml-schema-definition-tool-xsd-exe.md)k vygenerování tříd ze schématu, je vhodný atribut použit na člen typu String a jeho vlastnost **DataType** je nastavena na název datového typu XML. Například pokud schéma obsahuje element s názvem "MyToken" s datovým typem XML **NMTOKEN**, vygenerovaná třída může obsahovat člen, jak je znázorněno v následujícím příkladu.

```vb
<XmlElement(DataType:="NMTOKEN")> _
Public MyToken As String
```

```csharp
[XmlElement(DataType = "NMTOKEN")]
public string MyToken;
```

Podobně pokud vytváříte třídu, která musí odpovídat konkrétnímu schématu XML (XSD), měli byste použít příslušný atribut a nastavit jeho vlastnost **DataType** na požadovaný název datového typu XML.

Úplný seznam mapování typů naleznete v tématu vlastnost **DataType** pro libovolnou z následujících tříd atributů:

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
