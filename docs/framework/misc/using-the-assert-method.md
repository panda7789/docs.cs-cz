---
title: Použití metody Assert
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5799ab8e827305fca565064a0ae7290c6c19eb01
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463004"
---
# <a name="using-the-assert-method"></a><span data-ttu-id="c936f-102">Použití metody Assert</span><span class="sxs-lookup"><span data-stu-id="c936f-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="c936f-103"><xref:System.Security.CodeAccessPermission.Assert%2A> představuje metodu, která lze volat pro třídy oprávnění přístupu kódu a na <xref:System.Security.PermissionSet> třídy.</span><span class="sxs-lookup"><span data-stu-id="c936f-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="c936f-104">Můžete použít **Assert** povolit váš kód (a podřízené volající) k provedení akce, které váš kód má oprávnění k provedení, ale jeho volající nemusí mít oprávnění k provedení.</span><span class="sxs-lookup"><span data-stu-id="c936f-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="c936f-105">Kontrolní výraz zabezpečení změní normální proces, který modul runtime provádí během kontroly zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c936f-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="c936f-106">Pokud uplatňujete oprávnění, informuje systém zabezpečení není ke kontrole volajících váš kód s potvrzením oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c936f-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c936f-107">Kontrolní výrazy používejte opatrně, protože můžete otevřít bezpečnostní díry a narušují modul runtime mechanismus pro vynucení omezení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c936f-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="c936f-108">Kontrolní výrazy jsou užitečné v situacích, ve kterých knihovnu volání nespravovaného kódu nebo provede volání, která vyžaduje oprávnění, které samozřejmě nesouvisí s zamýšlené použití knihovny.</span><span class="sxs-lookup"><span data-stu-id="c936f-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="c936f-109">Například všechen spravovaný kód, který volá nespravovaný kód musí mít **SecurityPermission** s **požadavku na nespravovaný kód** příznak zadán.</span><span class="sxs-lookup"><span data-stu-id="c936f-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="c936f-110">Kód, který nepochází z místního počítače, jako je kód, který se stáhne z místní intranet, nebudou ve výchozím nastavení udělit toto oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c936f-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="c936f-111">Proto aby kód, který se stáhne z místního intranetu mohli volání knihovny, která používá nespravovaný kód, musí mít oprávnění s prohlašovanou knihovnou.</span><span class="sxs-lookup"><span data-stu-id="c936f-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="c936f-112">Kromě toho některé knihovny mohou provádět volání, která jsou viditelná pro volající a vyžadují zvláštní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c936f-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="c936f-113">Kontrolní výrazy můžete také použít v situacích, kdy váš kód přistupuje k prostředků tak, aby se zcela skryje volajícím.</span><span class="sxs-lookup"><span data-stu-id="c936f-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="c936f-114">Předpokládejme například, knihovny získává informace z databáze, ale v procesu také čte informace z registru počítače.</span><span class="sxs-lookup"><span data-stu-id="c936f-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="c936f-115">Protože vývojáři, kteří používají vaše knihovna nemají přístup ke zdroji, nemají žádnou možnost zjistit, že jejich kód vyžaduje **RegistryPermission** Chcete-li použít kód.</span><span class="sxs-lookup"><span data-stu-id="c936f-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="c936f-116">Pokud se rozhodnete, že není přiměřené nebo nezbytné vyžadují, aby volající kód oprávnění pro přístup k registru, v takovém případě můžete uplatnit oprávnění pro čtení registru.</span><span class="sxs-lookup"><span data-stu-id="c936f-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="c936f-117">V takovém případě je vhodné pro knihovny uplatnit oprávnění, tak že volající bez **RegistryPermission** můžete použít knihovnu.</span><span class="sxs-lookup"><span data-stu-id="c936f-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="c936f-118">Kontrolní výraz ovlivňuje procházení zásobníku pouze v případě, že s potvrzením oprávnění a oprávnění požadované podřízené volajícím jsou stejného typu a požadované oprávnění je podmnožinou s potvrzením oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c936f-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="c936f-119">Například, pokud uplatňujete **FileIOPermission** pro čtení všech souborů na jednotce C a podřízený požadavek se provádí **FileIOPermission** ke čtení v C:\Temp kontrolního výrazu by mohla ovlivnit procházení zásobníku; Nicméně pokud požadavek **FileIOPermission** pro zápis k jednotce C kontrolního výrazu by neměl žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="c936f-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="c936f-120">Pokud chcete provést kontrolní výrazy, musí váš kód udělit oprávnění uplatňujete a <xref:System.Security.Permissions.SecurityPermission> , která představuje práva ke kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="c936f-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="c936f-121">I když může uplatnit oprávnění, které nebylo uděleno kódu, bude kontrolního výrazu bezúčelné vzhledem k tomu, že kontrola zabezpečení by selhat, aby kontrolního výrazu by mohlo způsobit to proběhla úspěšně.</span><span class="sxs-lookup"><span data-stu-id="c936f-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="c936f-122">Následující obrázek znázorňuje, co se stane, když použijete **Assert**.</span><span class="sxs-lookup"><span data-stu-id="c936f-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="c936f-123">Předpokládejme, že následující tvrzení jsou pravdivá o sestavení A, B, C, E a F a dvě oprávnění, P1 a P1A:</span><span class="sxs-lookup"><span data-stu-id="c936f-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
-   <span data-ttu-id="c936f-124">P1A představuje oprávnění ke čtení souborů .txt na jednotce C:.</span><span class="sxs-lookup"><span data-stu-id="c936f-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
-   <span data-ttu-id="c936f-125">P1 představuje oprávnění ke čtení všech souborů na jednotce C:.</span><span class="sxs-lookup"><span data-stu-id="c936f-125">P1 represents the right to read all files on the C drive.</span></span>  
  
-   <span data-ttu-id="c936f-126">Jsou P1A i P1 **FileIOPermission** typy a P1A je podmnožinou P1.</span><span class="sxs-lookup"><span data-stu-id="c936f-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
-   <span data-ttu-id="c936f-127">Sestavení E a F bylo uděleno oprávnění P1A.</span><span class="sxs-lookup"><span data-stu-id="c936f-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
-   <span data-ttu-id="c936f-128">Sestavení C bylo uděleno oprávnění P1.</span><span class="sxs-lookup"><span data-stu-id="c936f-128">Assembly C has been granted P1 permission.</span></span>  
  
-   <span data-ttu-id="c936f-129">Sestavení A a B byla udělena oprávnění P1A ani P1.</span><span class="sxs-lookup"><span data-stu-id="c936f-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
-   <span data-ttu-id="c936f-130">Metoda A je obsažen v sestavení A, metoda B je obsažen v sestavení B a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c936f-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Diagram zobrazující průběh sestavení metody Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)    
  
 <span data-ttu-id="c936f-132">V tomto scénáři, metody A volá B, volá B, C, volání jazyka C E, volání E F. Metoda C uplatňuje oprávnění ke čtení souborů na jednotce C (oprávnění P1) a metoda E požaduje oprávnění ke čtení souborů .txt na jednotce C (oprávnění P1A).</span><span class="sxs-lookup"><span data-stu-id="c936f-132">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="c936f-133">Při vyžádání v F dochází za běhu, procházení zásobníku se provádí pro kontrolu oprávnění všech volajících F, počínaje E. E bylo uděleno oprávnění P1A tak procházení zásobníku pokračuje ke kontrole oprávnění C, kde je zjištěna kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="c936f-133">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="c936f-134">Vzhledem k tomu, že požadované oprávnění (P1A) je podmnožinou s potvrzením oprávnění (P1), procházení zásobníku se zastaví a kontrola zabezpečení automaticky proběhne úspěšně.</span><span class="sxs-lookup"><span data-stu-id="c936f-134">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="c936f-135">Není důležité, že sestavením A a B nebyla udělena oprávnění P1A.</span><span class="sxs-lookup"><span data-stu-id="c936f-135">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="c936f-136">Pomocí uplatňování P1, metoda jazyka C zajišťuje, že jeho volající neměly přístup k prostředku chráněny P1, i v případě, že volající nebylo uděleno oprávnění pro přístup k prostředku.</span><span class="sxs-lookup"><span data-stu-id="c936f-136">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="c936f-137">Pokud navrhujete knihovny tříd a třídu, má přístup k chráněnému prostředku, by ve většině případů provedete požadavek zabezpečení, že volající třídy mají příslušná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c936f-137">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="c936f-138">Pokud třída pak provede operaci pro které víte, většina volajících nebude mít oprávnění, a pokud jste ochotni nést odpovědnost za umožníte tím tyto volajícím volat kód, lze uplatnit oprávnění pomocí volání **Assert** metodu na objekt oprávnění, která představuje operaci kód provádí.</span><span class="sxs-lookup"><span data-stu-id="c936f-138">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="c936f-139">Pomocí **Assert** tímto způsobem umožňuje volajícím obvykle nedosáhli volat váš kód.</span><span class="sxs-lookup"><span data-stu-id="c936f-139">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="c936f-140">Proto pokud uplatňujete oprávnění, byste měli provést příslušná bezpečnostní kontroly předem zabránit vaše komponenta před zneužitím.</span><span class="sxs-lookup"><span data-stu-id="c936f-140">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="c936f-141">Předpokládejme například, že vysoce důvěryhodných knihovna tříd je metoda, která odstraní soubory.</span><span class="sxs-lookup"><span data-stu-id="c936f-141">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="c936f-142">Přistupuje k souboru voláním nespravovanou funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="c936f-142">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="c936f-143">Volající spustí váš kód **odstranit** metodu předáním názvu souboru, který má být odstraněna, C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="c936f-143">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="c936f-144">V rámci **odstranit** kódu vytvoří <xref:System.Security.Permissions.FileIOPermission> objekt reprezentující přístup pro zápis k C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="c936f-144">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="c936f-145">(Oprávnění k zápisu je potřebné k odstranění souboru). Kód poté vyvolá imperativní kontrola zabezpečení voláním **FileIOPermission** objektu **vyžádání** metody.</span><span class="sxs-lookup"><span data-stu-id="c936f-145">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="c936f-146">Pokud jeden z volající v zásobníku volání nemá žádné toto oprávnění, <xref:System.Security.SecurityException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="c936f-146">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="c936f-147">Pokud není vyvolána žádná výjimka, víte, že všichni volající nemá oprávnění k přístupu k C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="c936f-147">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="c936f-148">Protože si myslíte, že většina vašich volající nemá oprávnění pro přístup k nespravovaným kódem, váš kód poté vytvoří <xref:System.Security.Permissions.SecurityPermission> objekt, který představuje oprávnění pro volání nespravovaného kódu a volá objektu **Assert** metody.</span><span class="sxs-lookup"><span data-stu-id="c936f-148">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="c936f-149">Nakonec se volá nespravovanou funkci Win32 odstranit C:\Text.txt a vrátí řízení volajícímu.</span><span class="sxs-lookup"><span data-stu-id="c936f-149">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c936f-150">Je nutné zajistit, že váš kód v situacích, kdy může být použít jiný kód pro přístup k prostředku, který je chráněn oprávnění, které uplatňujete nepoužívá kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="c936f-150">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="c936f-151">Například v kódu, která zapisuje do souboru, jejíž název je zadán jako parametr volající by uplatnit **FileIOPermission** pro zápis do souborů, protože váš kód by být otevřený, aby zneužití třetí stranou.</span><span class="sxs-lookup"><span data-stu-id="c936f-151">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="c936f-152">Při použití imperativní syntaxe zabezpečení volání **Assert** metoda na více oprávnění ve stejné metody způsobí, že výjimka zabezpečení, která je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="c936f-152">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="c936f-153">Místo toho byste měli vytvořit **PermissionSet** objektu, předejte ji jednotlivá oprávnění chcete vyvolat a následně zavolat **Assert** metodu **PermissionSet** objekt.</span><span class="sxs-lookup"><span data-stu-id="c936f-153">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="c936f-154">Můžete volat **Assert** metodu více než jednou při použití syntaxe deklarativní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c936f-154">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="c936f-155">Následující příklad ukazuje deklarativní syntaxe pro přepsání zabezpečení ověří pomocí **Assert** metody.</span><span class="sxs-lookup"><span data-stu-id="c936f-155">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="c936f-156">Všimněte si, že **FileIOPermissionAttribute** syntaxe má dvě hodnoty: <xref:System.Security.Permissions.SecurityAction> výčet a umístění souboru nebo adresáři, do kterého má být udělena oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c936f-156">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="c936f-157">Volání **Assert** způsobí, že požadavky pro přístup k `C:\Log.txt` proběhla úspěšně, i když volající nejsou kontroluje oprávnění pro přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="c936f-157">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="c936f-158">Následující fragmenty kódu ukazují imperativní syntaxe pro přepsání zabezpečení ověří pomocí **Assert** metody.</span><span class="sxs-lookup"><span data-stu-id="c936f-158">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="c936f-159">V tomto příkladu instance **FileIOPermission** deklaraci objektu.</span><span class="sxs-lookup"><span data-stu-id="c936f-159">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="c936f-160">Je předán konstruktoru **FileIOPermissionAccess.AllAccess** definovat typ přístupu povolený, za nímž následuje řetězec, který popisuje umístění souboru.</span><span class="sxs-lookup"><span data-stu-id="c936f-160">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="c936f-161">Jednou **FileIOPermission** objekt je definovaný, je třeba volat jeho **Assert** metodu pro přepsání kontroly zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c936f-161">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c936f-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c936f-162">See also</span></span>
- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="c936f-163">Atributy</span><span class="sxs-lookup"><span data-stu-id="c936f-163">Attributes</span></span>](../../../docs/standard/attributes/index.md)
- [<span data-ttu-id="c936f-164">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="c936f-164">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
