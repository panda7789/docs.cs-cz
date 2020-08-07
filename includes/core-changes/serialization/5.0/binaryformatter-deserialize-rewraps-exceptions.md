---
ms.openlocfilehash: 2e9267b35c9389da017927aca2346190348265c9
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87919368"
---
### <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a><span data-ttu-id="04e63-101">BinaryFormatter. deserializace přebalí některé výjimky v SerializationException.</span><span class="sxs-lookup"><span data-stu-id="04e63-101">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>

<span data-ttu-id="04e63-102"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>Metoda teď znovu zabalí některé objekty výjimek uvnitř a <xref:System.Runtime.Serialization.SerializationException> před tím, než se výjimka rozšíří zpět volajícímu.</span><span class="sxs-lookup"><span data-stu-id="04e63-102">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method now rewraps some exception objects inside a <xref:System.Runtime.Serialization.SerializationException> before propagating the exception back to the caller.</span></span>

#### <a name="change-description"></a><span data-ttu-id="04e63-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="04e63-103">Change description</span></span>

<span data-ttu-id="04e63-104">Dřív <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> Metoda povolila nějaké libovolné výjimky, například <xref:System.ArgumentNullException> , k rozšíření zásobníku na jeho volající.</span><span class="sxs-lookup"><span data-stu-id="04e63-104">Previously, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method allowed some arbitrary exceptions, such as <xref:System.ArgumentNullException>, to propagate up the stack to its callers.</span></span>

<span data-ttu-id="04e63-105">V rozhraní .NET 5,0 a novějších <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> metod metoda lépe zachycuje výjimky, ke kterým dochází v důsledku neplatných operací deserializace a zabalí je do <xref:System.Runtime.Serialization.SerializationException> .</span><span class="sxs-lookup"><span data-stu-id="04e63-105">In .NET 5.0 and later, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method more aggressively catches exceptions that occur due to invalid deserialization operations and wraps them in a <xref:System.Runtime.Serialization.SerializationException>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="04e63-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="04e63-106">Version introduced</span></span>

<span data-ttu-id="04e63-107">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="04e63-107">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="04e63-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="04e63-108">Recommended action</span></span>

<span data-ttu-id="04e63-109">Ve většině případů není nutné provádět žádnou akci.</span><span class="sxs-lookup"><span data-stu-id="04e63-109">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="04e63-110">Nicméně pokud váš web volání závisí na vyvolání konkrétní výjimky, můžete zrušit zabalení výjimky z vnější <xref:System.Runtime.Serialization.SerializationException> , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="04e63-110">However, if your call site depends on a particular exception being thrown, you can unwrap the exception from the outer <xref:System.Runtime.Serialization.SerializationException>, as shown in the following example.</span></span>

```csharp
Stream inputStream = GetInputStream();
var formatter = new BinaryFormatter();

try
{
    object deserialized = formatter.Deserialize(inputStream);
}
catch (MyException myEx)
{
    // Handle 'myEx' here in case it was thrown directly.
}
catch (SerializationException serEx) when (serEx.InnerException is MyException myEx)
{
    // Handle 'myEx' here in case it was wrapped in SerializationException.
}
```

#### <a name="category"></a><span data-ttu-id="04e63-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="04e63-111">Category</span></span>

<span data-ttu-id="04e63-112">Serializace</span><span class="sxs-lookup"><span data-stu-id="04e63-112">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="04e63-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="04e63-113">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

-->
