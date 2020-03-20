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
ms.openlocfilehash: a0466eb5c24840c77a3b191f9b0e001f6b267fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181164"
---
# <a name="link-demands"></a><span data-ttu-id="037d9-102">Požadavky na odkaz</span><span class="sxs-lookup"><span data-stu-id="037d9-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="037d9-103">Požadavek na propojení způsobí kontrolu zabezpečení během kompilace just-in-time a zkontroluje pouze okamžité volající sestavení vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="037d9-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="037d9-104">K propojení dochází, když je váš kód vázán na odkaz na typ, včetně odkazů na ukazatel funkce a volání metody.</span><span class="sxs-lookup"><span data-stu-id="037d9-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="037d9-105">Pokud volající sestavení nemá dostatečná oprávnění k propojení s vaším kódem, odkaz není povolen a při načtení a spuštění kódu je vyvolána výjimka za běhu.</span><span class="sxs-lookup"><span data-stu-id="037d9-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="037d9-106">Požadavky na propojení mohou být přepsány ve třídách, které dědí z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="037d9-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="037d9-107">Všimněte si, že úplné procházení zásobníku se neprovádí s tímto typem poptávky a že váš kód je stále náchylný k lákavým útokům.</span><span class="sxs-lookup"><span data-stu-id="037d9-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="037d9-108">Například pokud je metoda v sestavení A chráněna požadavkem na propojení, je vyhodnocen přímý volající v sestavení B na základě oprávnění sestavení B.  Požadavek na propojení však nevyhodnotí metodu v sestavení C, pokud nepřímo volá metodu v sestavení A pomocí metody v sestavení B. Požadavek na propojení určuje pouze oprávnění, která musí mít přímí volající v sestavení okamžitého volání k propojení s vaším kódem.</span><span class="sxs-lookup"><span data-stu-id="037d9-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="037d9-109">Neurčuje oprávnění, která musí mít všichni volající ke spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="037d9-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="037d9-110"><xref:System.Security.CodeAccessPermission.Assert%2A>Modifikátory procházení a <xref:System.Security.CodeAccessPermission.PermitOnly%2A> procházení zásobníku nemají vliv na vyhodnocení požadavků na <xref:System.Security.CodeAccessPermission.Deny%2A>propojení.</span><span class="sxs-lookup"><span data-stu-id="037d9-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="037d9-111">Vzhledem k tomu, že požadavky na propojení neprovádějí procházení zásobníku, modifikátory procházení zásobníku nemají žádný vliv na požadavky na propojení.</span><span class="sxs-lookup"><span data-stu-id="037d9-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="037d9-112">Pokud metoda chráněná požadavek propojení je přístupná prostřednictvím [reflexe](../reflection-and-codedom/reflection.md), pak požadavek na propojení zkontroluje okamžitévolající kódu přistupovat prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="037d9-112">If a method protected by a link demand is accessed through [Reflection](../reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="037d9-113">To platí jak pro zjišťování metody a pro vyvolání metody provádí pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="037d9-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="037d9-114">Předpokládejme například, že kód <xref:System.Reflection.MethodInfo> používá reflexi k vrácení objektu představujícího metodu chráněnou požadavkem na propojení a poté předá tento objekt **MethodInfo** jinému kódu, který používá objekt k vyvolání původní metody.</span><span class="sxs-lookup"><span data-stu-id="037d9-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="037d9-115">V tomto případě dojde ke kontrole poptávky propojení dvakrát: jednou pro kód, který vrací Objekt **MethodInfo** a jednou pro kód, který jej vyvolá.</span><span class="sxs-lookup"><span data-stu-id="037d9-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="037d9-116">Požadavek na propojení prováděný na konstruktoru statické třídy nechrání konstruktor, protože statické konstruktory jsou volány systémem mimo cestu spuštění kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="037d9-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="037d9-117">V důsledku toho při použití požadavku propojení na celou třídu, nemůže chránit přístup ke statickékonstruktoru, i když chrání zbytek třídy.</span><span class="sxs-lookup"><span data-stu-id="037d9-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="037d9-118">Následující fragment kódu deklarativně určuje, `ReadData` že jakýkoli `CustomPermission` kód odkazující na metodu musí mít oprávnění.</span><span class="sxs-lookup"><span data-stu-id="037d9-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="037d9-119">Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="037d9-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="037d9-120">Požadavek je proveden předáním příznaku **SecurityAction.LinkDemand** na `CustomPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="037d9-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="037d9-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="037d9-121">See also</span></span>

- [<span data-ttu-id="037d9-122">Atributy</span><span class="sxs-lookup"><span data-stu-id="037d9-122">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="037d9-123">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="037d9-123">Code Access Security</span></span>](code-access-security.md)
