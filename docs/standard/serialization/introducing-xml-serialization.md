---
title: "Představení serializace XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 13afeecc979cab9719ffa063f78ff91c866262d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="introducing-xml-serialization"></a>Představení serializace XML
Serializace je proces převodu objektu do formuláře, který lze snadno přenést. Například může serializovat objekt a přenosu je prostřednictvím Internetu pomocí protokolu HTTP mezi klientem a serverem. Na druhém konci rekonstruuje deserializace objektu z datového proudu.  
  
 Serializace XML serializuje pouze veřejné pole a hodnoty vlastností objektu do datový proud XML. Serializace XML neobsahuje informace o typu. Pokud máte například **kniha** objekt, který existuje v **knihovny** oboru názvů není zaručeno, že je deserializovat do objektu stejného typu.  
  
> [!NOTE]
>  Serializace XML nepřevádět metody, indexery, soukromé pole nebo vlastnosti jen pro čtení (s výjimkou kolekce jen pro čtení). K serializaci všechny objektu polí a vlastností, veřejné a soukromé, použijte <xref:System.Runtime.Serialization.DataContractSerializer> namísto serializace XML.  
  
 Centrální třída v serializaci XML je <xref:System.Xml.Serialization.XmlSerializer> třídy a nejdůležitější metody v této třídě **serializace** a **Deserialize** metody. <xref:System.Xml.Serialization.XmlSerializer> Vytváří soubory jazyka C# a jejich kompiluje do soubory DLL a provést serializace. V rozhraní .NET Framework 2.0 [nástroje Generátor serializátor XML (Sgen.exe)](../../../docs/standard/serialization/xml-serializer-generator-tool-sgen-exe.md) je určena ke generování tyto sestavení serializace předem, chcete-li nasadit s vaší aplikací a zlepšit výkon při spuštění. Datový proud XML, které jsou generované **XmlSerializer** je kompatibilní s World Wide Web Consortium (www.w3.org) jazyk definice schématu XML (XSD) 1.0 doporučení. Kromě toho jsou typy dat, které jsou generovány kompatibilní s dokumentu s názvem "část schématu XML 2: datové typy."  
  
 Data ve vašich objektů je popsán pomocí programovacího jazyka konstrukce jako třídy, pole, vlastnosti, primitivní typy, pole a i embedded XML ve formě **XmlElement** nebo **XmlAttribute**objekty. Máte možnost vytvořit vlastní třídy označena s atributy, nebo pomocí nástroje definici schématu XML vygenerovat třídy založen na stávajícím schématu XML.  
  
 Pokud máte schématu XML, můžete spustit nástroj definici schématu XML k vytvoření sadu tříd, které jsou silného typu schématu a označena s atributy. Pokud instance této třídy serializován, generovaný XML dodržuje schématu XML. Za předpokladu tříd se můžete programovat proti snadno s ní manipulováno objektový model při zachování zajištěno, že generovaného kódu XML odpovídá schématu XML. Jde o alternativu k použití jiné třídy v rozhraní .NET Framework, jako **XmlReader** a **XmlWriter** třídy, analyzovat a zapisovat datový proud XML. Další informace najdete v tématu [XML – dokumenty a Data](../../../docs/standard/data/xml/index.md). Tyto třídy umožňují analyzovat jakékoli datový proud XML. Naproti tomu použít **XmlSerializer** očekávaného datový proud XML tak, aby odpovídala známé schématu XML.  
  
 Atributy řízení datový proud XML, které jsou generované **XmlSerializer** třídě, což vám umožní nastavit obor názvů XML, název elementu, název atributu a tak dále, datového proudu XML. Další informace o těchto atributů a jak se řídit serializace XML, najdete v části [řízení atributy pomocí serializace XML](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md). Pro tabulku těchto atributů, které jsou používány k ovládání generovaný soubor XML, najdete v části [atributy, řízení serializace XML](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md).  
  
 **XmlSerializer** třída může ještě víc serializovat objekt a generovat kódovaného datový proud XML protokolu SOAP. Vygenerovaný XML dodržuje část 5 W3c dokumentu s názvem "Simple Object Access Protocol (SOAP) 1.1." Další informace o tomto procesu najdete v tématu [postup: serializaci objektu jako datový proud XML SOAP-Encoded](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md). Tabulka atributů, které řídí generovaný soubor XML, najdete v části [atributy, řízení kódovaný SOAP serializace](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
 **XmlSerializer** třída generuje protokolu SOAP zprávy vytvořené a předaný webové služby XML. Chcete-li řídit zprávy protokolu SOAP, můžete použít atributy do třídy, vrácené hodnoty, parametry a pole nalezen v souboru XML webové služby (.asmx). Můžete použít atributy uvedené v "Atributy, aby ovládací prvek XML serializace" a "Atributy, aby ovládací prvek kódovaný SOAP serializace", protože webové služby XML lze použít buď literál nebo kódovaného protokolu SOAP stylu. Další informace o používání atributů k řízení XML generované webové služby XML, najdete v části [serializace XML pomocí webové služby XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md). Další informace o protokolu SOAP a XML webových služeb najdete v tématu [přizpůsobení protokolu SOAP zprávy](https://msdn.microsoft.com/en-us/subscriptions/index/dkwy2d72\(v=vs.71\).aspx).  
  
## <a name="security-considerations-for-xmlserializer-applications"></a>Důležité informace o zabezpečení pro XmlSerializer aplikace  
 Při vytvoření aplikace, která používá **XmlSerializer**, je třeba si uvědomit následující položky a jejich důsledky:  
  
-   **XmlSerializer** vytvoří C# (.cs), soubory a zpracovává je do souborů .dll v adresáři s názvem proměnnou prostředí TEMP; serializace dochází u těchto knihovny DLL.  
  
    > [!NOTE]
    >  Tyto sestavení serializace můžete předem vygenerovaných a podepsán pomocí nástroje SGen.exe. To nepomáhá serveru webové služby. Jinými slovy je pouze pro použití klienta a pro ruční serializaci.  
  
     Kód a knihoven DLL, která jsou citlivé na škodlivý proces v době vytvoření a sestavení. Používáte-li počítači se systémem Microsoft Windows NT 4.0 nebo novější, je možné, že dvě nebo více mohou uživatelé sdílet adresář TEMP. Sdílení dočasné složky je nebezpečné, pokud dva účty mají jiné bezpečnostní oprávnění a vyšší oprávnění účtu spouští aplikace pomocí **XmlSerializer**. V takovém případě jednoho uživatele, může porušení zabezpečení počítače v případě nahrazení souboru buď .cs nebo .dll, který se zkompiluje. Chcete-li tento problém odstranit, vždy ujistěte se, že každý účet v počítači má vlastní profil. Ve výchozím nastavení proměnná prostředí TEMP odkazuje na jiný adresář pro každý účet.  
  
-   Pokud uživatel se zlými úmysly odešle nepřetržitý proud dat XML do webového serveru (odepření služby), pak se **XmlSerializer** pokračuje ve zpracování dat, dokud se počítač spustí nízkou na prostředky.  
  
     Tento druh útoku se eliminují, pokud používáte počítač se systémem Internet Information Services (IIS) a je aplikace spuštěna v rámci služby IIS. Služba IIS obsahuje jako brána, který nezpracovává datových proudů delší než nastavené množství (výchozí hodnota je 4 KB). Pokud vytvoříte aplikaci, která nepoužívá službu IIS a deserializuje s **XmlSerializer**, měli byste implementovat podobné brány, která zabraňuje odepření služby.  
  
-   **XmlSerializer** serializuje data a spouští kód, pomocí libovolného typu uvedené.  
  
     V které škodlivý objekt představuje hrozbu dvěma způsoby. Spustí škodlivý kód nebo jej může vložit škodlivý kód do souboru C# vytvořené **XmlSerializer**. V případě, první Pokud škodlivý objekt se pokusí spustit proceduru destruktivních zabezpečení přístupu ke kódu zabraňuje škody prováděné. V druhém případě je teoretické možné, že škodlivý objekt může nějakým způsobem vložení kódu do souboru C# vytvořené **XmlSerializer**. I když má prověřit tento problém, důkladně a takového útoku je považován za pravděpodobné, byste měli vzít preventivní opatření nikdy serializace dat s typem neznámý a nedůvěryhodný.  
  
-   Serializovaná citlivá data může být ohrožena.  
  
     Po **XmlSerializer**má serializovat data, mohou být uloženy jako soubor XML nebo jiného úložiště dat. Pokud vaše úložiště dat je k dispozici pro procesy nebo je zobrazen v intranetu nebo Internetu, můžete data odcizení a záměrně použity. Například pokud vytvoříte aplikaci, která serializuje objednávky obsahující čísla kreditních karet, je velmi důvěrná data. K tomu nedocházelo, vždy chránit úložiště dat a proveďte kroky, které chcete zachovat privátní.  
  
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
  
 Další příklady serializace najdete v tématu [serializace XML Příklady](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
## <a name="items-that-can-be-serialized"></a>Položky, které lze serializovat  
 Následující položky lze serializovat pomocí **XmLSerializer** třídy:  
  
-   Vlastnosti veřejné čtení a zápis a pole veřejné třídy.  
  
-   Třídy implementující **ICollection** nebo **rozhraní IEnumerable**.  
  
    > [!NOTE]
    >  Pouze kolekce jsou serializovaná, není veřejné vlastnosti.  
  
-   **XmlElement** objekty.  
  
-   **XmlNode –** objekty.  
  
-   **Datová sada** objekty.  
  
 Další informace o serializaci nebo deserializaci objektů najdete v tématu [postup: serializovat objekt](../../../docs/standard/serialization/how-to-serialize-an-object.md) a [postup: deserializaci objektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md).  
  
## <a name="advantages-of-using-xml-serialization"></a>Výhody použití serializace XML  
 **XmlSerializer**třída poskytuje úplný a flexibilní kontrolu při serializaci objektu ve formátu XML. Pokud vytváříte webové služby XML, můžete použít atributy, které řídí serializace za účelem třídy a členy zajistit, že výstup kódu XML odpovídá určité schéma.  
  
 Například **XmlSerializer** umožňuje:  
  
-   Zadejte, zda pole nebo vlastnost by měla být zakódován jako atribut nebo element.  
  
-   Zadejte obor názvů XML používat.  
  
-   Zadejte název elementu nebo atributu, pokud je název pole nebo vlastnost nevhodný.  
  
 Další výhodou serializace XML je, zda máte bez omezení na aplikací, které vytvoříte, jako datový proud XML, který je generován odpovídá dané schéma. Představte si schématu, který slouží k popisu knihy. Nabízí nadpis, Autor, vydavatel a ISBN čísla elementu. Můžete vyvíjet aplikace, která zpracovává data XML v jakékoli požadovaným způsobem, například jako pořadí adresáře nebo jako inventáře knihy. V obou případech jediným požadavkem je, že datový proud XML odpovídá zadané schéma jazyka (XSD) definice schématu XML.  
  
## <a name="xml-serialization-considerations"></a>Důležité informace o serializaci XML  
 Následující by měly být považovány za při použití **XmlSerializer** třídy:  
  
-   Nástroj Sgen.exe je výslovně určena ke generování sestavení serializace pro optimální výkon.  
  
-   Serializovaná data obsahuje vlastní data a strukturu vaší třídy. Informace o typu identitu a sestavení nejsou zahrnuty.  
  
-   Pouze veřejné vlastnosti a pole lze serializovat. Vlastnosti musí mít veřejnou přistupující objekty (get a set metod). Pokud musí serializovat neveřejným dat, použijte <xref:System.Runtime.Serialization.DataContractSerializer> třídy a serializace XML.  
  
-   Třídu musí mít výchozí konstruktor bylo serializováno modulem **XmlSerializer**.  
  
-   Metody nelze serializovat.  
  
-   **XmlSerializer** může zpracovat třídy, které implementují **rozhraní IEnumerable** nebo **ICollection** odlišně, pokud nebudou splňovat určité požadavky následujícím způsobem.  
  
     Třídu, která implementuje **rozhraní IEnumerable** musí implementovat veřejné **přidat** metody, která přijímá jeden parametr. **Přidat** parametr metody musí být konzistentní (polymorfní) s typem vráceným z **IEnumerator.Current** vlastnost vrácená z **GetEnumerator** Metoda.  
  
     Třídu, která implementuje **ICollection** kromě **rozhraní IEnumerable** (například **CollectionBase**) musí mít veřejný **položky** indexované vlastnost (indexer v jazyce C#), která přebírá celé číslo a musí mít veřejný **počet** vlastnost typu **celé číslo**. Parametr předaný **přidat** metoda musí být stejného typu, který vrátil **položky** vlastnost nebo jeden z tohoto typu základů.  
  
     Pro třídy implementující **ICollection**, k serializaci hodnoty jsou načteny z indexované **položky** vlastnost spíše než voláním **GetEnumerator**. Navíc veřejná pole a vlastnosti nejsou serializované, s výjimkou veřejná pole, které vracejí jiné třídy kolekce (ten, který implementuje **ICollection**). Příklad, naleznete v části [serializace XML Příklady](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
## <a name="xsd-data-type-mapping"></a>Mapování typů dat XSD  
 W3c (www.w3.org) dokumentu s názvem "XML schématu část 2: datové typy" Určuje jednoduché datové typy, které jsou povoleny ve schématu schématu XML definice jazyk (XSD). Pro mnoho z těchto (například **int** a **decimal**), neexistuje odpovídající typ dat v rozhraní .NET Framework. Ale některé typy dat XML nemají odpovídající typ dat v rozhraní .NET Framework (například **NMTOKEN** datový typ). V takových případech, pokud použijete nástroj definice schématu XML ([nástroje definice schématu XML (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) ke generování třídy z schéma, je použit odpovídající atribut člena typu řetězec a jeho **datovýtyp** je nastavena na název datového typu XML. Například pokud schéma obsahuje element s názvem "MyToken" datového typu XML **NMTOKEN**, generovaná třída může obsahovat členem, jak je znázorněno v následujícím příkladu.  
  
```vb  
<XmlElement(DataType:="NMTOKEN")> _  
Public MyToken As String  
```  
  
```csharp  
[XmlElement(DataType = "NMTOKEN")]  
public string MyToken;  
```  
  
 Podobně, pokud vytváříte třídu, která musí odpovídat na konkrétní schématu XML (XSD), doporučujeme použít odpovídajícího atributu a nastavit jeho **datový typ** vlastnost k požadovaným datům XML zadejte název.  
  
 Úplný seznam mapování typu, najdete v článku **datový typ** vlastnost pro žádné z následujících tříd atributů:  
  
-   <xref:System.Xml.Serialization.SoapAttributeAttribute>  
  
-   <xref:System.Xml.Serialization.SoapElementAttribute>  
  
-   <xref:System.Xml.Serialization.XmlArrayItemAttribute>  
  
-   <xref:System.Xml.Serialization.XmlAttributeAttribute>  
  
-   <xref:System.Xml.Serialization.XmlElementAttribute>  
  
-   <xref:System.Xml.Serialization.XmlRootAttribute>  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Serialization.XmlSerializer>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.IO.FileStream>  
 [XML a serializace protokolu SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [Binární serializace](../../../docs/standard/serialization/binary-serialization.md)  
 [Serializace](../../../docs/standard/serialization/index.md)  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Příklady serializace XML](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 [Postupy: serializaci objektu](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Postupy: deserializaci objektu](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
