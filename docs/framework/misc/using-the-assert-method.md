---
title: Použití metody Assert
description: Podívejte se, jak můžete použít metodu Assert k povolení kódu (a kódu volajícího) k tomu, aby váš kód měl oprávnění, ale ne jeho volajících.
ms.date: 03/30/2017
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
ms.openlocfilehash: 573b84f991e795c2513f213ddb52999fef51c454
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855661"
---
# <a name="using-the-assert-method"></a><span data-ttu-id="e039d-103">Použití metody Assert</span><span class="sxs-lookup"><span data-stu-id="e039d-103">Using the Assert Method</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="e039d-104"><xref:System.Security.CodeAccessPermission.Assert%2A>je metoda, která může být volána u tříd oprávnění přístupu kódu a <xref:System.Security.PermissionSet> třídy.</span><span class="sxs-lookup"><span data-stu-id="e039d-104"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="e039d-105">Pomocí **výrazu Assert** můžete povolit váš kód (a volajícím) provádět akce, ke kterým má váš kód oprávnění, ale jeho volající nemusí mít oprávnění k tomu.</span><span class="sxs-lookup"><span data-stu-id="e039d-105">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="e039d-106">Kontrolní výraz zabezpečení mění běžný proces, který modul runtime provede během kontroly zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e039d-106">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="e039d-107">Pokud vyhodnotit oprávnění, sdělí systému zabezpečení, aby nekontroloval volající kód pro kontrolní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e039d-107">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="e039d-108">Používejte kontrolní výrazy pečlivě, protože mohou otevírat bezpečnostní otvory a podrušovat mechanismus modulu runtime pro vynucování omezení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e039d-108">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="e039d-109">Kontrolní výrazy jsou užitečné v situacích, kdy knihovna volá do nespravovaného kódu nebo provádí volání vyžadující oprávnění, které není zjevně související s zamýšleným použitím knihovny.</span><span class="sxs-lookup"><span data-stu-id="e039d-109">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="e039d-110">Například všechen spravovaný kód, který volá do nespravovaného kódu, musí mít **SecurityPermission** s určeným **příznakem** .</span><span class="sxs-lookup"><span data-stu-id="e039d-110">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="e039d-111">Kód, který nepochází z místního počítače, jako je například kód stažený z místního intranetu, nebude toto oprávnění ve výchozím nastavení uděleno.</span><span class="sxs-lookup"><span data-stu-id="e039d-111">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="e039d-112">Proto aby kód, který je stažen z místního intranetu, mohl volat knihovnu, která používá nespravovaný kód, musí mít oprávnění, které je pro knihovnu uplatněno.</span><span class="sxs-lookup"><span data-stu-id="e039d-112">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="e039d-113">Kromě toho mohou některé knihovny vyvolat volání, která jsou nepřesná volajícím a vyžadují zvláštní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e039d-113">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="e039d-114">Můžete také použít kontrolní výrazy v situacích, ve kterých váš kód přistupuje k prostředku způsobem, který je zcela skrytý od volajících.</span><span class="sxs-lookup"><span data-stu-id="e039d-114">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="e039d-115">Předpokládejme například, že vaše knihovna získává informace z databáze, ale v procesu také čte informace z registru počítače.</span><span class="sxs-lookup"><span data-stu-id="e039d-115">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="e039d-116">Vzhledem k tomu, že vývojáři, kteří používají vaši knihovnu, nemají přístup k vašemu zdroji, nemají žádný způsob, jak si poznáte, že jejich kód vyžaduje **RegistryPermission** , aby mohl váš kód použít.</span><span class="sxs-lookup"><span data-stu-id="e039d-116">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="e039d-117">V takovém případě, pokud se rozhodnete, že není přiměřené nebo nutné vyžadovat, aby volající vašeho kódu měli oprávnění pro přístup do registru, můžete uplatnit oprávnění pro čtení registru.</span><span class="sxs-lookup"><span data-stu-id="e039d-117">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="e039d-118">V této situaci je vhodné, aby knihovna mohla uplatnit oprávnění, aby volající bez **RegistryPermission** mohli použít knihovnu.</span><span class="sxs-lookup"><span data-stu-id="e039d-118">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="e039d-119">Kontrolní výraz ovlivňuje procházení zásobníku pouze v případě, že kontrolní oprávnění a oprávnění vyžádané volajícím jsou stejného typu a pokud je požadované oprávnění podmnožinou vyžádaného oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e039d-119">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="e039d-120">Například, pokud vyberete hodnotu **FileIOPermission** pro čtení všech souborů na jednotce C a pro datové jednotky **FileIOPermission** se provede požadavek na přečtení souborů v C:\Temp, může kontrolní výraz ovlivnit procházení zásobníku. Nicméně pokud byla poptávka pro **FileIOPermission** pro zápis do jednotky C, kontrolní výraz by neměl mít žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="e039d-120">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="e039d-121">Chcete-li provést kontrolní výrazy, váš kód musí mít udělené oprávnění a <xref:System.Security.Permissions.SecurityPermission> , které představuje právo k provedení kontrolního výrazu.</span><span class="sxs-lookup"><span data-stu-id="e039d-121">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="e039d-122">I když byste mohli vyhodnotit oprávnění, že váš kód nebyl udělen, kontrolní výraz by byl bezúčelné, protože ověření zabezpečení by mohlo selhat předtím, než může kontrolní výraz způsobit jeho úspěch.</span><span class="sxs-lookup"><span data-stu-id="e039d-122">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="e039d-123">Následující ilustrace ukazuje, co se stane, když použijete **Assert**.</span><span class="sxs-lookup"><span data-stu-id="e039d-123">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="e039d-124">Předpokládejme, že následující příkazy jsou pravdivé pro sestavení A, B, C, E a F a dvě oprávnění, P1 a P1A:</span><span class="sxs-lookup"><span data-stu-id="e039d-124">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
- <span data-ttu-id="e039d-125">P1A představuje právo číst soubory. txt na jednotce C.</span><span class="sxs-lookup"><span data-stu-id="e039d-125">P1A represents the right to read .txt files on the C drive.</span></span>  
  
- <span data-ttu-id="e039d-126">P1 představuje právo na čtení všech souborů na jednotce C.</span><span class="sxs-lookup"><span data-stu-id="e039d-126">P1 represents the right to read all files on the C drive.</span></span>  
  
- <span data-ttu-id="e039d-127">P1A a P1 jsou oba typy **FileIOPermission** a je P1A podmnožinou P1.</span><span class="sxs-lookup"><span data-stu-id="e039d-127">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
- <span data-ttu-id="e039d-128">Sestavením E a F byla udělena oprávnění P1A.</span><span class="sxs-lookup"><span data-stu-id="e039d-128">Assemblies E and F have been granted P1A permission.</span></span>  
  
- <span data-ttu-id="e039d-129">Sestavení C bylo uděleno oprávnění P1.</span><span class="sxs-lookup"><span data-stu-id="e039d-129">Assembly C has been granted P1 permission.</span></span>  
  
- <span data-ttu-id="e039d-130">Sestavení A a B byla udělena oprávnění P1 ani P1A.</span><span class="sxs-lookup"><span data-stu-id="e039d-130">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
- <span data-ttu-id="e039d-131">Metoda A je obsažena v sestavení A, metoda B je obsažena v sestavení B a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e039d-131">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Diagram, který znázorňuje sestavení metody Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 <span data-ttu-id="e039d-133">V tomto scénáři volá metoda A volání B, B volání jazyka C, volání jazyka C E a E volá F. Metoda C kontrolní výrazy oprávnění ke čtení souborů na jednotce C (oprávnění P1) a metoda E požaduje oprávnění ke čtení souborů. txt na jednotce C (oprávnění P1A).</span><span class="sxs-lookup"><span data-stu-id="e039d-133">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="e039d-134">V případě, že poptávka v F je zjištěna v době běhu, je provedeno procházení zásobníku pro kontrolu oprávnění všech volajících F, počínaje E. E byl uděleno oprávnění P1A, takže procházení zásobníku pokračuje v kontrole oprávnění jazyka C, kde je zjištěn kontrolní výraz C.</span><span class="sxs-lookup"><span data-stu-id="e039d-134">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="e039d-135">Vzhledem k tomu, že vyžádané oprávnění (P1A) je podmnožinou vyžádaného oprávnění (P1), procházení zásobníku se zastaví a Automatická kontroly zabezpečení se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="e039d-135">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="e039d-136">Nezáleží na tom, že sestavení A a B nemají udělena oprávnění P1A.</span><span class="sxs-lookup"><span data-stu-id="e039d-136">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="e039d-137">Vytvrzením P1, metoda C zaručí, že volající mají přístup k prostředku chráněnému P1, a to i v případě, že volajícímu nebylo uděleno oprávnění k přístupu k tomuto prostředku.</span><span class="sxs-lookup"><span data-stu-id="e039d-137">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="e039d-138">Pokud navrhujete knihovnu tříd a třída přistupuje k chráněnému prostředku, měli byste ve většině případů učinit požadavek zabezpečení vyžadující, aby volající třídy měly příslušné oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e039d-138">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="e039d-139">Pokud třída poté provede operaci, pro kterou víte, že většina volajících nebude mít oprávnění, a pokud jste ochotni vzít zodpovědnost za to, že volajícímu kódu budou volat, můžete uplatnit oprávnění voláním metody **Assert** na objekt oprávnění, který představuje operaci, kterou kód provádí.</span><span class="sxs-lookup"><span data-stu-id="e039d-139">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="e039d-140">Použití **výrazu Assert** tímto způsobem umožňuje volajícím, které obvykle nemohou provést volání vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="e039d-140">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="e039d-141">Proto pokud přiřadíte oprávnění, měli byste předem provést příslušné kontroly zabezpečení, aby nedošlo k nesprávnému použití vaší komponenty.</span><span class="sxs-lookup"><span data-stu-id="e039d-141">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="e039d-142">Předpokládejme například, že vaše vysoce důvěryhodná třída knihovny má metodu, která odstraňuje soubory.</span><span class="sxs-lookup"><span data-stu-id="e039d-142">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="e039d-143">Přistupuje k souboru voláním nespravované funkce Win32.</span><span class="sxs-lookup"><span data-stu-id="e039d-143">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="e039d-144">Volající vyvolá metodu **odstranění** kódu předáním názvu souboru, který má být odstraněn, C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="e039d-144">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="e039d-145">V rámci metody **Delete** váš kód vytvoří objekt, který <xref:System.Security.Permissions.FileIOPermission> představuje přístup pro zápis do C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="e039d-145">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="e039d-146">(K odstranění souboru se vyžaduje přístup pro zápis.) Váš kód poté vyvolá imperativní kontrolu zabezpečení voláním metody **Demand** objektu **FileIOPermission** .</span><span class="sxs-lookup"><span data-stu-id="e039d-146">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="e039d-147">Pokud jedno z volajících v zásobníku volání nemá toto oprávnění, <xref:System.Security.SecurityException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e039d-147">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="e039d-148">Pokud není vyvolána žádná výjimka, víte, že všichni volající mají právo na přístup k C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="e039d-148">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="e039d-149">Vzhledem k tomu, že většina vašich volajících nebude mít oprávnění pro přístup k nespravovanému kódu, váš kód pak vytvoří <xref:System.Security.Permissions.SecurityPermission> objekt, který představuje právo na volání nespravovaného kódu a volá metodu **Assert** objektu.</span><span class="sxs-lookup"><span data-stu-id="e039d-149">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="e039d-150">Nakonec volá nespravovanou funkci Win32 k odstranění C:\Text.txt a vrátí řízení volajícímu.</span><span class="sxs-lookup"><span data-stu-id="e039d-150">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="e039d-151">Musíte mít jistotu, že váš kód nepoužívá kontrolní výrazy v situacích, kdy váš kód může být použit jiným kódem pro přístup k prostředku, který je chráněn oprávněním, které uplatňujete.</span><span class="sxs-lookup"><span data-stu-id="e039d-151">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="e039d-152">Například v kódu, který zapisuje do souboru, jehož název je zadán volajícím jako parametr, neurčíte hodnotu **FileIOPermission** pro zápis do souborů, protože kód by byl otevřen pro zneužití třetí stranou.</span><span class="sxs-lookup"><span data-stu-id="e039d-152">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="e039d-153">Při použití imperativní syntaxe zabezpečení volání metody **Assert** u více oprávnění ve stejné metodě způsobí vyvolání výjimky zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e039d-153">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="e039d-154">Místo toho byste měli vytvořit objekt **PermissionSet** , předat jeho jednotlivá oprávnění, která chcete vyvolat, a pak zavolat metodu **Assert** na objekt **PermissionSet** .</span><span class="sxs-lookup"><span data-stu-id="e039d-154">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="e039d-155">Metodu **Assert** můžete zavolat více než jednou, pokud použijete deklarativní syntaxi zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e039d-155">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="e039d-156">Následující příklad ukazuje deklarativní syntaxi pro přepsání kontrol zabezpečení pomocí metody **Assert** .</span><span class="sxs-lookup"><span data-stu-id="e039d-156">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="e039d-157">Všimněte si, že syntaxe **FileIOPermissionAttribute** přebírá dvě hodnoty: <xref:System.Security.Permissions.SecurityAction> výčet a umístění souboru nebo adresáře, ke kterému má být uděleno oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e039d-157">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="e039d-158">Volání metody **Assert** způsobí, že požadavky pro přístup budou `C:\Log.txt` úspěšné, i když volajícím nejsou kontrolováni oprávnění k přístupu k souboru.</span><span class="sxs-lookup"><span data-stu-id="e039d-158">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="e039d-159">Následující fragmenty kódu ukazují imperativní syntaxi pro přepsání kontrol zabezpečení pomocí metody **Assert** .</span><span class="sxs-lookup"><span data-stu-id="e039d-159">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="e039d-160">V tomto příkladu je deklarována instance objektu **FileIOPermission** .</span><span class="sxs-lookup"><span data-stu-id="e039d-160">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="e039d-161">Jeho konstruktoru je předán **FileIOPermissionAccess. AllAccess** , který definuje typ povoleného přístupu následovaný řetězcem, který popisuje umístění souboru.</span><span class="sxs-lookup"><span data-stu-id="e039d-161">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="e039d-162">Po definování objektu **FileIOPermission** stačí volat jeho metodu **Assert** pro přepsání kontroly zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e039d-162">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e039d-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="e039d-163">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="e039d-164">Atributy</span><span class="sxs-lookup"><span data-stu-id="e039d-164">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="e039d-165">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="e039d-165">Code Access Security</span></span>](code-access-security.md)
