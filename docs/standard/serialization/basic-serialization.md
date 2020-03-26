---
title: Základní serializace
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: ce86f7897c5c117c4fd6f1eabc4c8b802103261c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248027"
---
# <a name="basic-serialization"></a><span data-ttu-id="7cf29-102">Základní serializace</span><span class="sxs-lookup"><span data-stu-id="7cf29-102">Basic serialization</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="7cf29-103">Nejjednodušší způsob, jak třídy serializovatelné je označit <xref:System.SerializableAttribute> ji následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="7cf29-103">The easiest way to make a class serializable is to mark it with the <xref:System.SerializableAttribute> as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
<span data-ttu-id="7cf29-104">Následující příklad kódu ukazuje, jak může být instance této třídy serializována do souboru.</span><span class="sxs-lookup"><span data-stu-id="7cf29-104">The following code example shows how an instance of this class can be serialized to a file.</span></span>  
  
```csharp  
MyObject obj = new MyObject();  
obj.n1 = 1;  
obj.n2 = 24;  
obj.str = "Some String";  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Create, FileAccess.Write, FileShare.None);  
formatter.Serialize(stream, obj);  
stream.Close();  
```  
  
<span data-ttu-id="7cf29-105">V tomto příkladu binární formátovací modul použije k serializaci.</span><span class="sxs-lookup"><span data-stu-id="7cf29-105">This example uses a binary formatter to do the serialization.</span></span> <span data-ttu-id="7cf29-106">Vše, co musíte udělat, je vytvořit instanci datového proudu a modul pro vytváření modulu umožňuje použít a potom volat **Serialize** metoda na modul pro vytváření forových kláves.</span><span class="sxs-lookup"><span data-stu-id="7cf29-106">All you need to do is create an instance of the stream and the formatter you intend to use, and then call the **Serialize** method on the formatter.</span></span> <span data-ttu-id="7cf29-107">Datový proud a objekt určený k serializaci jsou poskytovány jako parametry pro toto volání.</span><span class="sxs-lookup"><span data-stu-id="7cf29-107">The stream and the object to serialize are provided as parameters to this call.</span></span> <span data-ttu-id="7cf29-108">I když není ukázáno explicitně v tomto příkladu, bude serializována všechny proměnné členů třídy – i proměnné, které jsou označeny jako soukromé.</span><span class="sxs-lookup"><span data-stu-id="7cf29-108">Although it is not explicitly demonstrated in this example, all member variables of a class will be serialized—even variables marked as private.</span></span> <span data-ttu-id="7cf29-109">V tomto ohledu se binární serializace liší od <xref:System.Xml.Serialization.XmlSerializer> třídy, která pouze serializuje veřejná pole.</span><span class="sxs-lookup"><span data-stu-id="7cf29-109">In this aspect, binary serialization differs from the <xref:System.Xml.Serialization.XmlSerializer> class, which only serializes public fields.</span></span> <span data-ttu-id="7cf29-110">Informace o vyloučení členských proměnných z binární serializace naleznete v [tématu Selektivní serializace](selective-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="7cf29-110">For information on excluding member variables from binary serialization, see [Selective Serialization](selective-serialization.md).</span></span>  
  
<span data-ttu-id="7cf29-111">Obnovení objektu zpět do původní stavu je stejně jednoduché.</span><span class="sxs-lookup"><span data-stu-id="7cf29-111">Restoring the object back to its former state is just as easy.</span></span> <span data-ttu-id="7cf29-112">Nejprve vytvořte datový proud <xref:System.Runtime.Serialization.Formatter>pro čtení a a a potom dáte pokyn, aby modul pro formátování rekonstruoval objekt.</span><span class="sxs-lookup"><span data-stu-id="7cf29-112">First, create a stream for reading and a <xref:System.Runtime.Serialization.Formatter>, and then instruct the formatter to deserialize the object.</span></span> <span data-ttu-id="7cf29-113">Následující příklad kódu ukazuje, jak to lze provést.</span><span class="sxs-lookup"><span data-stu-id="7cf29-113">The code example below shows how this is done.</span></span>  
  
```csharp  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Open, FileAccess.Read, FileShare.Read);  
MyObject obj = (MyObject) formatter.Deserialize(stream);  
stream.Close();  
  
// Here's the proof.  
Console.WriteLine("n1: {0}", obj.n1);  
Console.WriteLine("n2: {0}", obj.n2);  
Console.WriteLine("str: {0}", obj.str);  
```  
  
<span data-ttu-id="7cf29-114">Výše <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> uvedené použité je velmi efektivní a vytváří kompaktní bajt ový proud.</span><span class="sxs-lookup"><span data-stu-id="7cf29-114">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> used above is very efficient and produces a compact byte stream.</span></span> <span data-ttu-id="7cf29-115">Všechny objekty serializované pomocí tohoto formátování lze deserializovat také s ním, díky čemuž je ideální nástroj pro serializaci objektů, které k deserializaci na rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7cf29-115">All objects serialized with this formatter can also be deserialized with it, which makes it an ideal tool for serializing objects that will be deserialized on the .NET Framework.</span></span> <span data-ttu-id="7cf29-116">Je důležité si všimnout, že konstruktory nejsou volána, když je objekt deserializován.</span><span class="sxs-lookup"><span data-stu-id="7cf29-116">It is important to note that constructors are not called when an object is deserialized.</span></span> <span data-ttu-id="7cf29-117">Toto omezení je umístěn na deserializace z hlediska výkonu.</span><span class="sxs-lookup"><span data-stu-id="7cf29-117">This constraint is placed on deserialization for performance reasons.</span></span> <span data-ttu-id="7cf29-118">Však to porušuje některé obvyklé smluv, které modul runtime provede pomocí objektu zapisovače a vývojáři se ujistěte, že znají důsledky při označení objektu jako serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="7cf29-118">However, this violates some of the usual contracts the runtime makes with the object writer, and developers should ensure that they understand the ramifications when marking an object as serializable.</span></span>  
  
<span data-ttu-id="7cf29-119">Pokud přenositelnost je požadavek, použijte <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> místo.</span><span class="sxs-lookup"><span data-stu-id="7cf29-119">If portability is a requirement, use the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> instead.</span></span> <span data-ttu-id="7cf29-120">Jednoduše nahradit **BinaryFormatter** ve výše uvedeném kódu **soapformatter** a volání **Serializovat** a **Deserializovat** jako dříve.</span><span class="sxs-lookup"><span data-stu-id="7cf29-120">Simply replace the **BinaryFormatter** in the code above with **SoapFormatter,** and call **Serialize** and **Deserialize** as before.</span></span> <span data-ttu-id="7cf29-121">Tento formátovací modul vytváří následující výstup například využité nad.</span><span class="sxs-lookup"><span data-stu-id="7cf29-121">This formatter produces the following output for the example used above.</span></span>  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:a1="http://schemas.microsoft.com/clr/assem/ToFile">  
  
  <SOAP-ENV:Body>  
    <a1:MyObject id="ref-1">  
      <n1>1</n1>  
      <n2>24</n2>  
      <str id="ref-3">Some String</str>  
    </a1:MyObject>  
  </SOAP-ENV:Body>  
</SOAP-ENV:Envelope>  
```  
  
<span data-ttu-id="7cf29-122">Je důležité si uvědomit, že [serializovatelný](xref:System.SerializableAttribute) atribut nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="7cf29-122">It's important to note that the [Serializable](xref:System.SerializableAttribute) attribute cannot be inherited.</span></span> <span data-ttu-id="7cf29-123">Je-li odvodit novou třídu z `MyObject`, musí být označen nové třídy s atributem také nebo nemůže být serializován.</span><span class="sxs-lookup"><span data-stu-id="7cf29-123">If you derive a new class from `MyObject`, the new class must be marked with the attribute as well, or it cannot be serialized.</span></span> <span data-ttu-id="7cf29-124">Například při pokusu o serializaci instance třídy níže, dostanete <xref:System.Runtime.Serialization.SerializationException> s informací, `MyStuff` že typ není označen jako serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="7cf29-124">For example, when you attempt to serialize an instance of the class below, you'll get a <xref:System.Runtime.Serialization.SerializationException> informing you that the `MyStuff` type is not marked as serializable.</span></span>  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 <span data-ttu-id="7cf29-125">Použití [Serializable](xref:System.SerializableAttribute) atribut je vhodné, ale má omezení, jak bylo dříve prokázáno.</span><span class="sxs-lookup"><span data-stu-id="7cf29-125">Using the [Serializable](xref:System.SerializableAttribute) attribute is convenient, but it has limitations as previously demonstrated.</span></span> <span data-ttu-id="7cf29-126">Informace o tom, kdy byste měli označit třídu pro serializaci, naleznete v pokynech pro [serializaci.](serialization-guidelines.md)</span><span class="sxs-lookup"><span data-stu-id="7cf29-126">Refer to the [Serialization Guidelines](serialization-guidelines.md) for information about when you should mark a class for serialization.</span></span> <span data-ttu-id="7cf29-127">Serializaci nelze přidat do třídy po kompilaci.</span><span class="sxs-lookup"><span data-stu-id="7cf29-127">Serialization cannot be added to a class after it has been compiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf29-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cf29-128">See also</span></span>

- [<span data-ttu-id="7cf29-129">Binární serializace</span><span class="sxs-lookup"><span data-stu-id="7cf29-129">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="7cf29-130">Serializace XML a SOAP</span><span class="sxs-lookup"><span data-stu-id="7cf29-130">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
