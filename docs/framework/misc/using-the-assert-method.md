---
title: "Použití metody Assert"
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
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a1627af9dd968a8a183a251d5352c62457f71e27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-assert-method"></a><span data-ttu-id="899fa-102">Použití metody Assert</span><span class="sxs-lookup"><span data-stu-id="899fa-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="899fa-103"><xref:System.Security.CodeAccessPermission.Assert%2A>představuje metodu, kterou lze volat na kód přístupové oprávnění třídy a na <xref:System.Security.PermissionSet> třídy.</span><span class="sxs-lookup"><span data-stu-id="899fa-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="899fa-104">Můžete použít **Assert** aby váš kód (a podřízené volající) k provedení akce, které má oprávnění k provedení kódu, ale jeho volající nemusí mít oprávnění k provedení.</span><span class="sxs-lookup"><span data-stu-id="899fa-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="899fa-105">Kontrolní výraz zabezpečení změní normální proces, který modul runtime provádí během kontroly zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="899fa-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="899fa-106">Pokud uplatňujete oprávnění, říká systému zabezpečení není ke kontrole volající kódu pro uplatňovaná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="899fa-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="899fa-107">Kontrolní výrazy používejte opatrně, protože mohou otevřít bezpečnostní díry a narušují modul runtime mechanismus pro vynucení omezení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="899fa-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="899fa-108">Kontrolní výrazy jsou užitečné v situacích, ve kterých knihovna volání nespravovaného kódu nebo provádí volání, které vyžaduje oprávnění, která nesouvisí se samozřejmě se zamýšlené použití této knihovny.</span><span class="sxs-lookup"><span data-stu-id="899fa-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="899fa-109">Například všechny spravované kód, který musí mít volání nespravovaného kódu **SecurityPermission** s **UnmanagedCode** příznak.</span><span class="sxs-lookup"><span data-stu-id="899fa-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="899fa-110">Kód, který nepochází z místního počítače, jako je například kód, který byl stažen z místního intranetu, nebudou ve výchozím nastavení udělit toto oprávnění.</span><span class="sxs-lookup"><span data-stu-id="899fa-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="899fa-111">Proto aby kód, který byl stažen z místního intranetu, abyste mohli volání knihovny, která používá nespravovaného kódu, musí mít oprávnění prosazený knihovny.</span><span class="sxs-lookup"><span data-stu-id="899fa-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="899fa-112">Kromě toho některé knihovny mohou provádět volání, která jsou viditelná pro volající a vyžadují zvláštní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="899fa-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="899fa-113">Můžete také použít kontrolní výrazy v situacích, ve kterých kódu přistupuje k prostředku způsobem, který je úplně skrytá volajícím.</span><span class="sxs-lookup"><span data-stu-id="899fa-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="899fa-114">Předpokládejme například, vaše knihovna získává informace z databáze, ale v procesu také čte informace z registru počítače.</span><span class="sxs-lookup"><span data-stu-id="899fa-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="899fa-115">Protože vývojáře, kteří používají vaše knihovna nemají přístup ke zdroji, nemají žádný způsob, jejich kód vyžaduje **RegistryPermission** Chcete-li použít kód.</span><span class="sxs-lookup"><span data-stu-id="899fa-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="899fa-116">Pokud se rozhodnete, že není přiměřené nebo nezbytné vyžadovat, aby volající kódu mají oprávnění pro přístup do registru, můžete v tomto případě uplatnit oprávnění pro čtení v registru.</span><span class="sxs-lookup"><span data-stu-id="899fa-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="899fa-117">V takovém případě je vhodné pro knihovnu, která má uplatnit oprávnění tak, že volající bez **RegistryPermission** můžete použít knihovnu.</span><span class="sxs-lookup"><span data-stu-id="899fa-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="899fa-118">Kontrolní výraz ovlivňuje procházení zásobníku pouze v případě, že uplatňovaná oprávnění a oprávnění pro název podřízený volající jsou stejného typu a požadované oprávnění je podmnožinou uplatňovaná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="899fa-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="899fa-119">Například, pokud uplatňujete **FileIOPermission** pro čtení všech souborů na jednotce C a podřízený požadavek se provádí **FileIOPermission** ke čtení souborů v C:\Temp, mohou ovlivnit kontrolní výraz procházení zásobníku; ale pokud byl požadavek na **FileIOPermission** k zápisu na disk C, kontrolní výraz by mít žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="899fa-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="899fa-120">Pokud chcete provést kontrolní výrazy, musí váš kód udělit oprávnění uplatňujete a <xref:System.Security.Permissions.SecurityPermission> představující práva ke kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="899fa-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="899fa-121">I když může uplatňovat oprávnění, které nebylo uděleno kódu, kontrolní výraz by zbytečný, protože kontrola zabezpečení by selhat, než kontrolní výraz by mohl způsobit ho proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="899fa-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="899fa-122">Následující obrázek znázorňuje, co se stane, když používáte **Assert**.</span><span class="sxs-lookup"><span data-stu-id="899fa-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="899fa-123">Předpokládejme, že se o sestavení A, B, C, E a F a dvě oprávnění P1 a P1A platí následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="899fa-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
-   <span data-ttu-id="899fa-124">P1A představuje práva ke čtení na jednotce C soubory s příponou .txt.</span><span class="sxs-lookup"><span data-stu-id="899fa-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
-   <span data-ttu-id="899fa-125">P1 představuje práva ke čtení všech souborů na jednotce C.</span><span class="sxs-lookup"><span data-stu-id="899fa-125">P1 represents the right to read all files on the C drive.</span></span>  
  
-   <span data-ttu-id="899fa-126">P1A a P1 jsou obě **FileIOPermission** typy a P1A je podmnožinou P1.</span><span class="sxs-lookup"><span data-stu-id="899fa-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
-   <span data-ttu-id="899fa-127">Sestavení E a F bylo uděleno oprávnění P1A.</span><span class="sxs-lookup"><span data-stu-id="899fa-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
-   <span data-ttu-id="899fa-128">Sestavení C bylo uděleno oprávnění P1.</span><span class="sxs-lookup"><span data-stu-id="899fa-128">Assembly C has been granted P1 permission.</span></span>  
  
-   <span data-ttu-id="899fa-129">Sestavení A a B byla udělena oprávnění P1 ani P1A.</span><span class="sxs-lookup"><span data-stu-id="899fa-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
-   <span data-ttu-id="899fa-130">Metoda A je obsažena v sestavení A, metoda B je obsažena v sestavení B a tak dále.</span><span class="sxs-lookup"><span data-stu-id="899fa-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 <span data-ttu-id="899fa-131">![](../../../docs/framework/misc/media/assert.gif "Assert")</span><span class="sxs-lookup"><span data-stu-id="899fa-131">![](../../../docs/framework/misc/media/assert.gif "assert")</span></span>  
<span data-ttu-id="899fa-132">Použití metody Assert</span><span class="sxs-lookup"><span data-stu-id="899fa-132">Using Assert</span></span>  
  
 <span data-ttu-id="899fa-133">V tomto scénáři, volání metod A B, B volání jazyka C, C volání E a volání E F. Metoda C uplatňuje oprávnění ke čtení souborů na jednotce C (oprávnění P1) a metoda E požaduje oprávnění ke čtení soubory s příponou .txt na jednotce C (oprávnění P1A).</span><span class="sxs-lookup"><span data-stu-id="899fa-133">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="899fa-134">Vyžádání v F vyskytne v době běhu, procházení zásobníku se provede na zkontrolujte oprávnění všech volajících F, počínaje E. E byla udělena oprávnění P1A tak procházení zásobníku pokračuje zkontrolujte oprávnění C, kde je zjištěno kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="899fa-134">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="899fa-135">Protože požadované oprávnění (P1A) je podmnožinou uplatňovaná oprávnění (P1), procházení zásobníku se zastaví a kontrola zabezpečení automaticky úspěšné.</span><span class="sxs-lookup"><span data-stu-id="899fa-135">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="899fa-136">Že sestavením A a B nebylo uděleno oprávnění P1A nezáleží.</span><span class="sxs-lookup"><span data-stu-id="899fa-136">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="899fa-137">Pomocí uplatňování P1, metoda C zajišťuje jeho volající přístup k prostředku chráněného P1, i v případě, že volající nebylo uděleno oprávnění pro přístup k prostředku.</span><span class="sxs-lookup"><span data-stu-id="899fa-137">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="899fa-138">Pokud návrh knihovny tříd a třída přistupuje k chráněnému prostředku, musí, ve většině případů provedete požadavek zabezpečení vyžaduje, aby volající třídy měli příslušné oprávnění.</span><span class="sxs-lookup"><span data-stu-id="899fa-138">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="899fa-139">Pokud třída potom provádí operaci, pro které znáte většina volajících nebude mít oprávnění, a pokud jste ochotni převzít odpovědnost za to, že umožníte těmto volajícím volat váš kód, můžete uplatnit oprávnění voláním **Assert** metoda na objekt oprávnění, která představuje operaci provádí kód.</span><span class="sxs-lookup"><span data-stu-id="899fa-139">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="899fa-140">Pomocí **Assert** tímto způsobem umožňuje volajícím za normálních okolností nemohli volat vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="899fa-140">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="899fa-141">Proto pokud uplatňujete oprávnění, byste měli být nutné provést vhodné kontroly zabezpečení předem zabránit zneužitím příslušné součásti.</span><span class="sxs-lookup"><span data-stu-id="899fa-141">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="899fa-142">Předpokládejme například, že vysoce důvěryhodná knihovna tříd má metodu, která odstraní soubory.</span><span class="sxs-lookup"><span data-stu-id="899fa-142">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="899fa-143">Voláním nespravované Win32 funkce přistupuje k souboru.</span><span class="sxs-lookup"><span data-stu-id="899fa-143">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="899fa-144">Volající spustí váš kód **odstranit** metodu předáním názvu souboru, který má být odstraněna, C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="899fa-144">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="899fa-145">V rámci **odstranit** metoda, vytvoří kód <xref:System.Security.Permissions.FileIOPermission> objekt reprezentující přístup pro zápis do C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="899fa-145">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="899fa-146">(Přístup pro zápis je nutné pro odstranění souboru). Váš kód poté vyvolá imperativní kontrolu zabezpečení voláním **FileIOPermission** objektu **vyžádání** metoda.</span><span class="sxs-lookup"><span data-stu-id="899fa-146">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="899fa-147">Pokud jeden z volajících v zásobníku volání nemá toto oprávnění, <xref:System.Security.SecurityException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="899fa-147">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="899fa-148">Pokud nedojde k výjimce, víte, že všechny volající mají oprávnění k přístupu k C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="899fa-148">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="899fa-149">Vzhledem k tomu, že budete mít dojem, že většina z vašich volajících nebude mít oprávnění pro přístup k nespravovanému kódu, váš kód poté vytvoří <xref:System.Security.Permissions.SecurityPermission> objekt, který reprezentuje právo pro volání nespravovaného kódu a zavolá metodu objektu **Assert** metoda.</span><span class="sxs-lookup"><span data-stu-id="899fa-149">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="899fa-150">Nakonec volá funkci nespravované Win32 odstranit C:\Text.txt a vrátí prvek na volajícího.</span><span class="sxs-lookup"><span data-stu-id="899fa-150">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="899fa-151">Je nutné zajistit, že váš kód nepoužívá kontrolní výrazy v situacích, kdy může být použít jiný kód pro přístup k prostředku, který je chráněný pomocí oprávnění, které uplatňujete.</span><span class="sxs-lookup"><span data-stu-id="899fa-151">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="899fa-152">Například v kódu, který zapisuje do souboru, jehož název je zadán volající jako parametr, nebude uplatnit **FileIOPermission** pro zápis do souborů, protože váš kód by být otevřené pro zneužití třetí strany.</span><span class="sxs-lookup"><span data-stu-id="899fa-152">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="899fa-153">Při použití imperativní syntaxe zabezpečení volání **Assert** metoda na více oprávnění ve stejnou metodu způsobí vyvolání výjimky zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="899fa-153">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="899fa-154">Místo toho, měli byste vytvořit **Assert** objektu, předejte ji chcete vyvolat a pak zavolají jednotlivá oprávnění **Assert** metodu **Assert** objekt.</span><span class="sxs-lookup"><span data-stu-id="899fa-154">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="899fa-155">Můžete volat **Assert** metoda více než jednou, když používáte deklarativní syntaxi zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="899fa-155">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="899fa-156">Následující příklad ukazuje deklarativní syntaxe pro používání kontroly přepsání zabezpečení **Assert** metoda.</span><span class="sxs-lookup"><span data-stu-id="899fa-156">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="899fa-157">Všimněte si, že **FileIOPermissionAttribute** syntaxe má dvě hodnoty: <xref:System.Security.Permissions.SecurityAction> výčet a umístění soubor nebo adresář, do kterého má být udělena oprávnění.</span><span class="sxs-lookup"><span data-stu-id="899fa-157">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="899fa-158">Volání **Assert** způsobí, že požadavky pro přístup k `C:\Log.txt` úspěšné, i když nejsou kontrola volající oprávnění k přístupu k souboru.</span><span class="sxs-lookup"><span data-stu-id="899fa-158">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub   
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {     
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}   
```  
  
 <span data-ttu-id="899fa-159">Následující fragmenty kódu ukazují imperativní syntaxi pro přepsání zabezpečení zkontroluje pomocí **Assert** metoda.</span><span class="sxs-lookup"><span data-stu-id="899fa-159">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="899fa-160">V tomto příkladu instanci **FileIOPermission** objekt deklarován.</span><span class="sxs-lookup"><span data-stu-id="899fa-160">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="899fa-161">Jeho konstruktoru je předán **FileIOPermissionAccess.AllAccess** k definování typu přístupová oprávnění, následuje řetězec popisující umístění souboru.</span><span class="sxs-lookup"><span data-stu-id="899fa-161">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="899fa-162">Jednou **FileIOPermission** objekt je definován, je třeba volat jeho **Assert** metodu pro přepsání kontroly zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="899fa-162">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");   
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="899fa-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="899fa-163">See Also</span></span>  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.SecurityPermission>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.Permissions.SecurityAction>  
 [<span data-ttu-id="899fa-164">Atributy</span><span class="sxs-lookup"><span data-stu-id="899fa-164">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="899fa-165">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="899fa-165">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
