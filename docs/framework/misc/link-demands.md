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
ms.openlocfilehash: 31fbd938acb457a4ea803375d18cb1be11d8b287
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217172"
---
# <a name="link-demands"></a><span data-ttu-id="8a5d6-102">Požadavky na odkaz</span><span class="sxs-lookup"><span data-stu-id="8a5d6-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="8a5d6-103">Požadavek propojení způsobí kontrolu zabezpečení během kompilace za běhu a kontroluje pouze okamžité volání sestavení kódu.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="8a5d6-104">Propojení nastane, pokud je váš kód svázán s odkazem na typ, včetně odkazů na ukazatel funkce a volání metod.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="8a5d6-105">Pokud volající sestavení nemá dostatečná oprávnění pro odkazování na váš kód, není odkaz povolen a výjimka za běhu je vyvolána, když je kód načten a spuštěn.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="8a5d6-106">Požadavky na propojení lze přepsat v třídách, které dědí z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="8a5d6-107">Všimněte si, že se s tímto typem požadavku neprovádí kompletní procházení zásobníku a že váš kód je stále náchylný k luring útokům.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="8a5d6-108">Například pokud je metoda v sestavení A chráněna požadavkem propojení, je přímý volající v sestavení B vyhodnocován na základě oprávnění sestavení B.  Požadavek propojení však nevyhodnotí metodu v sestavení C, pokud nepřímo volá metodu v sestavení A pomocí metody v sestavení B. Požadavek propojení určuje pouze oprávnění přímí volající v bezprostředním volajícím sestavení musí mít odkaz na váš kód.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="8a5d6-109">Neurčuje oprávnění, která všichni volající musí mít ke spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="8a5d6-110">Modifikátory procházení zásobníku <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>a <xref:System.Security.CodeAccessPermission.PermitOnly%2A> neovlivňují vyhodnocení požadavků propojení.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="8a5d6-111">Vzhledem k tomu, že požadavky na propojení neprovádějí procházení zásobníku, modifikátory procházení zásobníku nemají žádný vliv na požadavky propojení.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="8a5d6-112">Pokud je metoda chráněná požadavkem propojení k dispozici prostřednictvím [reflexe](../reflection-and-codedom/reflection.md), pak požadavek na propojení zkontroluje bezprostředního volajícího kódu, ke kterému se přistupoval prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-112">If a method protected by a link demand is accessed through [Reflection](../reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="8a5d6-113">To platí jak pro zjišťování metod, tak pro volání metod prováděná pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="8a5d6-114">Předpokládejme například, že kód používá reflexi k vrácení objektu <xref:System.Reflection.MethodInfo> reprezentujícího metodu chráněnou požadavkem propojení a pak předá tento objekt **MethodInfo** nějakému jinému kódu, který používá objekt k vyvolání původní metody.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="8a5d6-115">V tomto případě proběhne ověření požadavku propojení dvakrát: jednou pro kód, který vrátí objekt **MethodInfo** a jednou pro kód, který ho vyvolá.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a5d6-116">Požadavek propojení prováděný u konstruktoru statické třídy nechrání konstruktor, protože statické konstruktory jsou volány systémem, mimo cestu spuštění kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="8a5d6-117">V důsledku toho, pokud je požadavek na propojení aplikován na celou třídu, nemůže chránit přístup ke statickému konstruktoru, i když chrání zbytek třídy.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="8a5d6-118">Následující fragment kódu deklarativně určuje, že jakýkoli kód spojující metodu `ReadData` musí mít oprávnění `CustomPermission`.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="8a5d6-119">Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="8a5d6-120">Požadavek je proveden předáním příznaku **SecurityAction. LinkDemand** do `CustomPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="8a5d6-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8a5d6-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a5d6-121">See also</span></span>

- [<span data-ttu-id="8a5d6-122">Atributy</span><span class="sxs-lookup"><span data-stu-id="8a5d6-122">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="8a5d6-123">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="8a5d6-123">Code Access Security</span></span>](code-access-security.md)
