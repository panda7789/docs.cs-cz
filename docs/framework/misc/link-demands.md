---
title: Požadavky na odkaz
description: Přečtěte si o požadavcích na propojení, které způsobují kontrolu zabezpečení během kompilace JIT (just-in-time), a prostudujte pouze okamžité volání sestavení kódu.
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
ms.openlocfilehash: cd89c4ef27abb92fba567a1f3b490cb9d78fdddd
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86282053"
---
# <a name="link-demands"></a><span data-ttu-id="4da91-103">Požadavky na odkaz</span><span class="sxs-lookup"><span data-stu-id="4da91-103">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="4da91-104">Požadavek propojení způsobí kontrolu zabezpečení během kompilace za běhu a kontroluje pouze okamžité volání sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="4da91-104">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="4da91-105">Propojení nastane, pokud je váš kód svázán s odkazem na typ, včetně odkazů na ukazatel funkce a volání metod.</span><span class="sxs-lookup"><span data-stu-id="4da91-105">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="4da91-106">Pokud volající sestavení nemá dostatečná oprávnění pro odkazování na váš kód, není odkaz povolen a výjimka za běhu je vyvolána, když je kód načten a spuštěn.</span><span class="sxs-lookup"><span data-stu-id="4da91-106">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="4da91-107">Požadavky na propojení lze přepsat v třídách, které dědí z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="4da91-107">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="4da91-108">Všimněte si, že se s tímto typem požadavku neprovádí kompletní procházení zásobníku a že váš kód je stále náchylný k luring útokům.</span><span class="sxs-lookup"><span data-stu-id="4da91-108">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="4da91-109">Například pokud je metoda v sestavení A chráněna požadavkem propojení, je přímý volající v sestavení B vyhodnocován na základě oprávnění sestavení B.  Požadavek propojení však nevyhodnotí metodu v sestavení C, pokud nepřímo volá metodu v sestavení A pomocí metody v sestavení B. Požadavek propojení určuje pouze oprávnění přímí volající v bezprostředním volajícím sestavení musí mít odkaz na váš kód.</span><span class="sxs-lookup"><span data-stu-id="4da91-109">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="4da91-110">Neurčuje oprávnění, která všichni volající musí mít ke spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="4da91-110">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="4da91-111"><xref:System.Security.CodeAccessPermission.Assert%2A> <xref:System.Security.CodeAccessPermission.Deny%2A> <xref:System.Security.CodeAccessPermission.PermitOnly%2A> Modifikátory procházení zásobníku, a nejsou ovlivněny vyhodnocením požadavků propojení.</span><span class="sxs-lookup"><span data-stu-id="4da91-111">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="4da91-112">Vzhledem k tomu, že požadavky na propojení neprovádějí procházení zásobníku, modifikátory procházení zásobníku nemají žádný vliv na požadavky propojení.</span><span class="sxs-lookup"><span data-stu-id="4da91-112">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="4da91-113">Pokud je metoda chráněná požadavkem propojení k dispozici prostřednictvím [reflexe](../reflection-and-codedom/reflection.md), pak požadavek na propojení zkontroluje bezprostředního volajícího kódu, ke kterému se přistupoval prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="4da91-113">If a method protected by a link demand is accessed through [Reflection](../reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="4da91-114">To platí jak pro zjišťování metod, tak pro volání metod prováděná pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="4da91-114">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="4da91-115">Předpokládejme například, že kód používá reflexi k vrácení objektu, který <xref:System.Reflection.MethodInfo> představuje metodu chráněnou požadavkem propojení a poté předá tento objekt **MethodInfo** do nějakého jiného kódu, který používá objekt k vyvolání původní metody.</span><span class="sxs-lookup"><span data-stu-id="4da91-115">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="4da91-116">V tomto případě proběhne ověření požadavku propojení dvakrát: jednou pro kód, který vrátí objekt **MethodInfo** a jednou pro kód, který ho vyvolá.</span><span class="sxs-lookup"><span data-stu-id="4da91-116">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4da91-117">Požadavek propojení prováděný u konstruktoru statické třídy nechrání konstruktor, protože statické konstruktory jsou volány systémem, mimo cestu spuštění kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="4da91-117">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="4da91-118">V důsledku toho, pokud je požadavek na propojení aplikován na celou třídu, nemůže chránit přístup ke statickému konstruktoru, i když chrání zbytek třídy.</span><span class="sxs-lookup"><span data-stu-id="4da91-118">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="4da91-119">Následující fragment kódu deklarativně určuje, že jakýkoli kód spojující `ReadData` metodu musí mít `CustomPermission` oprávnění.</span><span class="sxs-lookup"><span data-stu-id="4da91-119">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="4da91-120">Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4da91-120">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="4da91-121">Požadavek je proveden předáním příznaku **SecurityAction. LinkDemand** do `CustomPermissionAttribute` .</span><span class="sxs-lookup"><span data-stu-id="4da91-121">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4da91-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="4da91-122">See also</span></span>

- [<span data-ttu-id="4da91-123">Atributy</span><span class="sxs-lookup"><span data-stu-id="4da91-123">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="4da91-124">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="4da91-124">Code Access Security</span></span>](code-access-security.md)
