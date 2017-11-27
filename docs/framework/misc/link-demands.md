---
title: "Požadavky na odkaz"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: faeeabeda89ea233e67b66b8848f5bbb665d3804
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="link-demands"></a><span data-ttu-id="0657a-102">Požadavky na odkaz</span><span class="sxs-lookup"><span data-stu-id="0657a-102">Link Demands</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="0657a-103">Požadavek propojení způsobí, že kontrola zabezpečení během kompilace za běhu a zkontroluje pouze okamžité volání sestavení vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="0657a-103">A link demand causes a security check during just-in-time compilation and checks only the immediate calling assembly of your code.</span></span> <span data-ttu-id="0657a-104">Propojování nastane, když kód je vázána na odkaz na typ, včetně odkazů ukazatel funkce a volání metod.</span><span class="sxs-lookup"><span data-stu-id="0657a-104">Linking occurs when your code is bound to a type reference, including function pointer references and method calls.</span></span> <span data-ttu-id="0657a-105">Pokud volajícího sestavení nemá dostatečná oprávnění k propojení kódu, není povolena na odkaz a výjimku modulu runtime je vyvolána, pokud kód je načíst a spustit.</span><span class="sxs-lookup"><span data-stu-id="0657a-105">If the calling assembly does not have sufficient permission to link to your code, the link is not allowed and a runtime exception is thrown when the code is loaded and run.</span></span> <span data-ttu-id="0657a-106">Požadavky na odkaz může být přepsána nastaveními v tříd, které dědí z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="0657a-106">Link demands can be overridden in classes that inherit from your code.</span></span>  
  
 <span data-ttu-id="0657a-107">Všimněte si, že s tímto typem vyžádání neprovádí se procházení úplné zásobníku a váš kód je přesto náchylné k útokům luring.</span><span class="sxs-lookup"><span data-stu-id="0657a-107">Note that a full stack walk is not performed with this type of demand and that your code is still susceptible to luring attacks.</span></span> <span data-ttu-id="0657a-108">Například pokud metoda v sestavení A chráněn požadavek propojení, přímý volající v sestavení B je vyhodnotit na základě oprávnění sestavení B.  Požadavek propojení však nevyhodnotí metodu v sestavení C, pokud nepřímo volá metodu v sestavení pomocí metody v sestavení B. Požadavek propojení určuje, že pouze oprávnění přímých volajících v okamžité volání sestavení musí mít k propojení kódu.</span><span class="sxs-lookup"><span data-stu-id="0657a-108">For example, if a method in assembly A is protected by a link demand, a direct caller in assembly B is evaluated based on the permissions of Assembly B.  However, the link demand will not evaluate a method in assembly C if it indirectly calls the method in assembly A using the method in assembly B. The link demand specifies only the permissions direct callers in the immediate calling assembly must have to link to your code.</span></span> <span data-ttu-id="0657a-109">Neurčuje oprávnění všechny volající musí mít pro spouštění vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="0657a-109">It does not specify the permissions all callers must have to run your code.</span></span>  
  
 <span data-ttu-id="0657a-110"><xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, A <xref:System.Security.CodeAccessPermission.PermitOnly%2A> modifikátory průchodu zásobníkem neovlivní hodnocení požadavků propojení.</span><span class="sxs-lookup"><span data-stu-id="0657a-110">The <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A>, and <xref:System.Security.CodeAccessPermission.PermitOnly%2A> stack walk modifiers do not affect the evaluation of link demands.</span></span>  <span data-ttu-id="0657a-111">Protože požadavky na odkaz neprovádět procházení zásobníku, Modifikátory průchodu zásobníkem nemají žádný vliv na požadavky na odkaz.</span><span class="sxs-lookup"><span data-stu-id="0657a-111">Because link demands do not perform a stack walk, the stack walk modifiers have no effect on link demands.</span></span>  
  
 <span data-ttu-id="0657a-112">Pokud je metoda chráněna požadavkem propojení přistupuje prostřednictvím [reflexe](../../../docs/framework/reflection-and-codedom/reflection.md), pak požadavek propojení zkontroluje bezprostředního volajícího kódu přistupovat prostřednictvím reflexe.</span><span class="sxs-lookup"><span data-stu-id="0657a-112">If a method protected by a link demand is accessed through [Reflection](../../../docs/framework/reflection-and-codedom/reflection.md), then a link demand checks the immediate caller of the code accessed through reflection.</span></span> <span data-ttu-id="0657a-113">To platí pro metody zjišťování i pro volání metody provést pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="0657a-113">This is true both for method discovery and for method invocation performed using reflection.</span></span> <span data-ttu-id="0657a-114">Předpokládejme například, že kód používá reflexe vrátit <xref:System.Reflection.MethodInfo> objekt představující metodu chráněnou požadavkem propojení a potom předá který **MethodInfo** objekt, který má jiný kód, který používá objekt k vyvolání původní metody.</span><span class="sxs-lookup"><span data-stu-id="0657a-114">For example, suppose code uses reflection to return a <xref:System.Reflection.MethodInfo> object representing a method protected by a link demand and then passes that **MethodInfo** object to some other code that uses the object to invoke the original method.</span></span> <span data-ttu-id="0657a-115">V takovém případě ověření požadavku propojení nastane dvakrát: jednou pro kód, který vrátí **MethodInfo** objekt a jednou pro kód, který vyvolá ho.</span><span class="sxs-lookup"><span data-stu-id="0657a-115">In this case the link demand check occurs twice: once for the code that returns the **MethodInfo** object and once for the code that invokes it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0657a-116">Požadavek propojení v konstruktoru statická třída provést nechrání konstruktoru, protože statické konstruktory jsou volány systému mimo cestu provádění kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0657a-116">A link demand performed on a static class constructor does not protect the constructor because static constructors are called by the system, outside the application's code execution path.</span></span> <span data-ttu-id="0657a-117">V důsledku toho při požadavku na propojení k celou třídu, nelze chránit přístup k statického konstruktoru, přestože chrání zbytek třídy.</span><span class="sxs-lookup"><span data-stu-id="0657a-117">As a result, when a link demand is applied to an entire class, it cannot protect access to a static constructor, although it does protect the rest of the class.</span></span>  
  
 <span data-ttu-id="0657a-118">Následující fragment kódu deklarativně určuje, že jakékoli propojení do kódu `ReadData` metoda musí mít `CustomPermission` oprávnění.</span><span class="sxs-lookup"><span data-stu-id="0657a-118">The following code fragment declaratively specifies that any code linking to the `ReadData` method must have the `CustomPermission` permission.</span></span> <span data-ttu-id="0657a-119">Toto oprávnění je hypotetické vlastní oprávnění a neexistuje v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0657a-119">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="0657a-120">Požadavek je vytvořen pomocí předání **SecurityAction.LinkDemand** příznak, který `CustomPermissionAttribute`.</span><span class="sxs-lookup"><span data-stu-id="0657a-120">The demand is made by passing a **SecurityAction.LinkDemand** flag to the `CustomPermissionAttribute`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0657a-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="0657a-121">See Also</span></span>  
 [<span data-ttu-id="0657a-122">Atributy</span><span class="sxs-lookup"><span data-stu-id="0657a-122">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="0657a-123">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="0657a-123">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
