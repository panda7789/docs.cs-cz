---
title: Požadavky na odkaz
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ba3172b1a82c0a9f624a49eb63a193dd29faac1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750730"
---
# <a name="link-demands"></a><span data-ttu-id="2def2-102">Požadavky na odkaz</span><span class="sxs-lookup"><span data-stu-id="2def2-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="2def2-103">Požadavek na propojení způsobí, že kontrola zabezpečení během kompilace just-in-time a zkontroluje pouze okamžitého volajícího sestavení vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="2def2-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="2def2-104">Propojení nastane, pokud váš kód je vázán na odkaz na typ, včetně odkazů na ukazatel funkce a volání metody.</span><span class="sxs-lookup"><span data-stu-id="2def2-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="2def2-105">Pokud volající sestavení nemá dostatečná oprávnění k propojení vašeho kódu, na odkaz není povolen a je vyvolána výjimka za běhu, když je načten a spustit kód.</span><span class="sxs-lookup"><span data-stu-id="2def2-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="2def2-106">Požadavky propojení lze přepsat ve třídách, které dědí z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="2def2-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="2def2-107">Všimněte si, že se neprovede úplné zásobníku s tímto typem vyžádání a že váš kód je přesto náchylné k útokům luring.</span><span class="sxs-lookup"><span data-stu-id="2def2-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="2def2-108">Například pokud metodu v sestavení A je chráněn pomocí požadavku propojení, přímému volajícímu v sestavení B je vyhodnotí na základě oprávnění sestavení B.  Ale požadavek propojení nebude vyhodnotit metodu v sestavení C nepřímo volá metodu v sestavení pomocí metody v sestavení B. Požadavek propojení určuje že jenom oprávnění přímý volající v okamžitého volajícího sestavení musí mít odkaz na váš kód.</span><span class="sxs-lookup"><span data-stu-id="2def2-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="2def2-109">Neurčuje oprávnění všichni volající musí mít pro spouštění vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="2def2-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="2def2-110"><xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, A <xref:System.Security.CodeAccessPermission.PermitOnly%2A> zásobníku funkce walk modifikátory nemají vliv na hodnocení požadavků propojení.</span><span class="sxs-lookup"><span data-stu-id="2def2-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="2def2-111">Protože požadavky propojení neprovádějte procházení zásobníku, modifikátory procházení zásobníku nemají žádný vliv na požadavky propojení.</span><span class="sxs-lookup"><span data-stu-id="2def2-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="2def2-112">Pokud metoda chráněn pomocí požadavku propojení je přístupný prostřednictvím [reflexe](../../../docs/framework/reflection-and-codedom/reflection.md), pak požadavek propojení kontroluje okamžitého volajícího kódu přístupné prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="2def2-112">If a method protected by a link demand is accessed through [Reflection](../../../docs/framework/reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="2def2-113">To platí pro metody zjišťování a pro volání metody provést pomocí operace reflection.</span><span class="sxs-lookup"><span data-stu-id="2def2-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="2def2-114">Předpokládejme například, že kód používá reflexi se vraťte <xref:System.Reflection.MethodInfo> objekt představující metodu chráněn pomocí požadavku propojení a potom předává, který **MethodInfo** objektu na jiný kód, který používá objekt volání původní metody.</span><span class="sxs-lookup"><span data-stu-id="2def2-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="2def2-115">V tomto případě ověření požadavku propojení dojde k dvakrát: jednou pro kód, který vrátí **MethodInfo** objekt a jednou pro kód, který vyvolá ji.</span><span class="sxs-lookup"><span data-stu-id="2def2-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2def2-116">Požadavek propojení provést ve statickém konstruktoru třídy nechrání konstruktoru, protože statické konstruktory jsou volány aplikací systému mimo cesta provádění kódu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="2def2-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="2def2-117">V důsledku toho při požadavku na propojení platí pro celou třídu, nemůže chránit přístup k statický konstruktor, přestože chrání zbytek třídy.</span><span class="sxs-lookup"><span data-stu-id="2def2-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="2def2-118">Následující fragment kódu deklarativně určuje, že jakékoli propojení do kódu `ReadData` metoda musí mít `CustomPermission` oprávnění.</span><span class="sxs-lookup"><span data-stu-id="2def2-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="2def2-119">Toto oprávnění je hypotetický vlastní oprávnění a neexistuje v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2def2-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="2def2-120">Předáním je vznesen požadavek **SecurityAction.LinkDemand** příznak, který `CustomPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="2def2-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function    
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2def2-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2def2-121">See also</span></span>

- [<span data-ttu-id="2def2-122">Atributy</span><span class="sxs-lookup"><span data-stu-id="2def2-122">Attributes</span></span>](../../../docs/standard/attributes/index.md)
- [<span data-ttu-id="2def2-123">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="2def2-123">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
