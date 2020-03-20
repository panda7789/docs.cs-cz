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
ms.openlocfilehash: 92e49af78d42f360d5798a72d4e7b981295947e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181108"
---
# <a name="using-the-assert-method"></a><span data-ttu-id="5b5ac-102">Použití metody Assert</span><span class="sxs-lookup"><span data-stu-id="5b5ac-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="5b5ac-103"><xref:System.Security.CodeAccessPermission.Assert%2A>je metoda, která může být volána na <xref:System.Security.PermissionSet> třídy oprávnění přístupu kódu a na třídu.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="5b5ac-104">Assert můžete **použít** k povolení kódu (a příjem volajících) k provádění akcí, které váš kód má oprávnění k provedení, ale jeho volající nemusí mít oprávnění k tomu.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="5b5ac-105">Kontrolní výraz zabezpečení změní normální proces, který za běhu provádí během kontroly zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="5b5ac-106">Když uplatníte oprávnění, řekne systému zabezpečení, aby nekontroloval volající vašeho kódu pro uplatněné oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="5b5ac-107">Kontrolní výrazy používejte opatrně, protože mohou otevřít bezpečnostní díry a ohrozit mechanismus běhu runtime pro vynucení bezpečnostních omezení.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="5b5ac-108">Kontrolní výrazy jsou užitečné v situacích, ve kterých knihovna volá do nespravovaného kódu nebo volání, které vyžaduje oprávnění, které zjevně nesouvisí s zamýšlené použití knihovny.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="5b5ac-109">Například všechny spravované kódy, které volají do nespravovaného kódu, musí mít **oprávnění Zabezpečení s** určeným příznakem **UnmanagedCode.**</span><span class="sxs-lookup"><span data-stu-id="5b5ac-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="5b5ac-110">Kód, který nepochází z místního počítače, jako je například kód stažený z místní sítě intranet, nebude ve výchozím nastavení uděleno toto oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="5b5ac-111">Proto aby kód, který je stažen z místnísítě intranet, aby bylo možné volat knihovnu, která používá nespravovaný kód, musí mít oprávnění uplatněné knihovnou.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="5b5ac-112">Některé knihovny mohou navíc volat volajícím, které nejsou viditelné a vyžadují zvláštní oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="5b5ac-113">Kontrolní výrazy můžete také použít v situacích, ve kterých váš kód přistupuje k prostředku způsobem, který je zcela skrytý před volajícími.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="5b5ac-114">Předpokládejme například, že knihovna získává informace z databáze, ale v procesu také čte informace z registru počítače.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="5b5ac-115">Vzhledem k tomu, že vývojáři, kteří používají vaši knihovnu, nemají přístup k vašemu zdroji, nemají žádný způsob, jak zjistit, že jejich kód vyžaduje **Oprávnění registru,** aby mohli používat váš kód.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="5b5ac-116">V takovém případě, pokud se rozhodnete, že není rozumné nebo nutné vyžadovat, aby volající kódu měli oprávnění k přístupu do registru, můžete uplatnit oprávnění ke čtení registru.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="5b5ac-117">V takovém případě je vhodné pro knihovnu uplatnit oprávnění tak, aby volající bez **RegistryPermission** můžete použít knihovnu.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="5b5ac-118">Kontrolní výraz ovlivňuje procházení zásobníku pouze v případě, že uplatněné oprávnění a oprávnění požadované volajícím navazujícím vysíláním jsou stejného typu a pokud je požadované oprávnění podmnožinou uplatněného oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="5b5ac-119">Pokud například uplatníte **oprávnění FileIOPermission** ke čtení všech souborů na jednotce C a pro FileIOPermission je požadováno, aby **fileiOPermission** četl soubory v C:\Temp, kontrolní výraz může ovlivnit procházení zásobníku; pokud však požadavek byl pro **FileIOPermission** zapisovat na jednotku C, kontrolní výraz by mít žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="5b5ac-120">Chcete-li provést kontrolní výrazy, musí být vašemu <xref:System.Security.Permissions.SecurityPermission> kódu uděleno oprávnění, které uplatňujete, a to, které představuje právo provádět kontrolní výrazy.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="5b5ac-121">I když můžete uplatnit oprávnění, že váš kód nebyl udělen, kontrolní výraz by bylo zbytečné, protože kontrola zabezpečení by se nezdaří dříve, než kontrolní výraz může způsobit jeho úspěšné.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="5b5ac-122">Následující obrázek znázorňuje, co se stane při použití **assert**.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="5b5ac-123">Předpokládejme, že následující příkazy jsou pravdivé o sestaveních A, B, C, E a F a dvou oprávnění, P1 a P1A:</span><span class="sxs-lookup"><span data-stu-id="5b5ac-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
- <span data-ttu-id="5b5ac-124">P1A představuje právo číst soubory TXT na jednotce C.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
- <span data-ttu-id="5b5ac-125">P1 představuje právo číst všechny soubory na jednotce C.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-125">P1 represents the right to read all files on the C drive.</span></span>  
  
- <span data-ttu-id="5b5ac-126">P1A a P1 jsou oba **typy FileIOPermission** a P1A je podmnožinou P1.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
- <span data-ttu-id="5b5ac-127">Sestavením E a F bylo uděleno oprávnění P1A.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
- <span data-ttu-id="5b5ac-128">Sestavení C bylo uděleno oprávnění P1.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-128">Assembly C has been granted P1 permission.</span></span>  
  
- <span data-ttu-id="5b5ac-129">Sestavení A a B nebyla udělena oprávnění P1 ani P1A.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
- <span data-ttu-id="5b5ac-130">Metoda A je obsažena v sestavě A, metoda B je obsažena v sestavě B a tak dále.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Diagram, který znázorňuje sestavení metody Assert.](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 <span data-ttu-id="5b5ac-132">V tomto scénáři metoda A volá B, B volá C, C volání E a E volání F. Metoda C uplatňuje oprávnění ke čtení souborů na jednotce C (oprávnění P1) a metoda E vyžaduje oprávnění ke čtení souborů TXT na jednotce C (oprávnění P1A).</span><span class="sxs-lookup"><span data-stu-id="5b5ac-132">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="5b5ac-133">Při požadavku v F je zjištěna v době běhu, procházení zásobníku se provádí ke kontrole oprávnění všech volajících F, počínaje E. E bylo uděleno oprávnění P1A, takže procházení zásobníku pokračuje zkoumat oprávnění C, kde je zjištěn kontrolní výraz C.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-133">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="5b5ac-134">Vzhledem k tomu, že požadované oprávnění (P1A) je podmnožinou uplatňovaného oprávnění (P1), procházení zásobníku se zastaví a kontrola zabezpečení se automaticky ustřídá.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-134">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="5b5ac-135">Nezáleží na tom, že sestavení A a B nebyla udělena oprávnění P1A.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-135">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="5b5ac-136">Uplatněním P1, metoda C zajišťuje, že jeho volající přístup k prostředku chráněnép1, i v případě, že volající mnebyla udělena oprávnění k přístupu k tomuto prostředku.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-136">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="5b5ac-137">Pokud navrhujete knihovnu tříd a třída přistupuje k chráněnému prostředku, měli byste ve většině případů vytvořit požadavek zabezpečení vyžadující, aby volající třídy měli příslušná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-137">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="5b5ac-138">Pokud třída pak provede operaci, pro kterou víte, že většina jeho volajících nebude mít oprávnění, a pokud jste ochotni převzít odpovědnost za to, že tito volající volají váš kód, můžete uplatnit oprávnění voláním metody **Assert** na objektu oprávnění, který představuje operaci, kterou kód provádí.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-138">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="5b5ac-139">Použití **Assert** tímto způsobem umožňuje volajícím, které obvykle nemůže tak učinit volání kódu.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-139">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="5b5ac-140">Pokud tedy uplatňujete oprávnění, měli byste předem provést příslušné kontroly zabezpečení, abyste zabránili zneužití součásti.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-140">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="5b5ac-141">Předpokládejme například, že vaše vysoce důvěryhodná třída knihovny má metodu, která odstraňuje soubory.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-141">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="5b5ac-142">Přistupuje k souboru voláním nespravované funkce Win32.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-142">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="5b5ac-143">Volající vyvolá metodu **Delete** vašeho kódu a předá název souboru, který má být odstraněn, C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-143">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="5b5ac-144">V rámci **Delete** metoda vytvoří <xref:System.Security.Permissions.FileIOPermission> objekt představující přístup pro zápis do C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-144">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="5b5ac-145">(K odstranění souboru je nutný přístup pro zápis.) Váš kód pak vyvolá imperativní kontrolu zabezpečení voláním metody **Demand** objektu **FileIOPermission.**</span><span class="sxs-lookup"><span data-stu-id="5b5ac-145">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="5b5ac-146">Pokud jeden z volajících v zásobníku volání nemá <xref:System.Security.SecurityException> toto oprávnění, je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-146">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="5b5ac-147">Pokud není vyvolána žádná výjimka, víte, že všichni volající mají právo na přístup k c:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-147">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="5b5ac-148">Vzhledem k tomu, že se domníváte, že většina volajících <xref:System.Security.Permissions.SecurityPermission> nebude mít oprávnění k přístupu k nespravovanému kódu, váš kód pak vytvoří objekt, který představuje právo volat nespravovaný kód a volá metodu **Assert** objektu.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-148">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="5b5ac-149">Nakonec volá nespravovanou funkci Win32 k odstranění c:\Text.txt a vrátí ovládací prvek volajícímu.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-149">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="5b5ac-150">Musíte si být jisti, že váš kód nepoužívá kontrolní výrazy v situacích, kdy váš kód může být použit jiným kódem pro přístup k prostředku, který je chráněn oprávněním, které uplatňujete.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-150">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="5b5ac-151">Například v kódu, který zapisuje do souboru, jehož jméno je určeno volajícím jako parametr, byste neuplatnili **FileIOPermission** pro zápis do souborů, protože váš kód by byl otevřen zneužití třetí stranou.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-151">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="5b5ac-152">Při použití imperativní syntaxe zabezpečení volání **Assert** metoda na více oprávnění ve stejné metodě způsobí, že výjimku zabezpečení, které mají být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-152">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="5b5ac-153">Místo toho byste měli vytvořit Objekt **PermissionSet,** předat mu jednotlivá oprávnění, která chcete vyvolat, a pak volat metodu **Assert** na objektu **PermissionSet.**</span><span class="sxs-lookup"><span data-stu-id="5b5ac-153">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="5b5ac-154">Při použití deklarativní syntaxe zabezpečení můžete volat metodu **Assert** více než jednou.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-154">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="5b5ac-155">Následující příklad ukazuje deklarativní syntaxi pro přepsání kontrol zabezpečení pomocí metody **Assert.**</span><span class="sxs-lookup"><span data-stu-id="5b5ac-155">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="5b5ac-156">Všimněte si, že syntaxe **FileIOPermissionAttribute** má dvě hodnoty: <xref:System.Security.Permissions.SecurityAction> výčet a umístění souboru nebo adresáře, ke kterému má být uděleno oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-156">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="5b5ac-157">Volání **Assert** způsobí, že `C:\Log.txt` požadavky na přístup k úspěšné, i když volající nejsou kontrolovány oprávnění pro přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-157">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="5b5ac-158">Následující fragmenty kódu zobrazují imperativní syntaxi pro přepsání kontrol zabezpečení pomocí metody **Assert.**</span><span class="sxs-lookup"><span data-stu-id="5b5ac-158">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="5b5ac-159">V tomto příkladu je deklarována instance objektu **FileIOPermission.**</span><span class="sxs-lookup"><span data-stu-id="5b5ac-159">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="5b5ac-160">Jeho konstruktor je předán **FileIOPermissionAccess.AllAccess** definovat typ přístupu povoleno, následuje řetězec popisující umístění souboru.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-160">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="5b5ac-161">Jakmile je objekt **FileIOPermission** definován, stačí pouze volat **jeho** assert metodu přepsat kontrolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5b5ac-161">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b5ac-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b5ac-162">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="5b5ac-163">Atributy</span><span class="sxs-lookup"><span data-stu-id="5b5ac-163">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="5b5ac-164">Zabezpečení přístupu kódu</span><span class="sxs-lookup"><span data-stu-id="5b5ac-164">Code Access Security</span></span>](code-access-security.md)
