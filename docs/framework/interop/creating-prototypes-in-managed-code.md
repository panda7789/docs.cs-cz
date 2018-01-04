---
title: "Vytváření prototypů ve spravovaném kódu"
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
- cpp
helpviewer_keywords:
- prototypes in managed code
- COM interop, DLL functions
- unmanaged functions
- platform invoke, creating prototypes
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, object fields
- DLL functions
- object fields in platform invoke
ms.assetid: ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9a85da0d1714c263b446c88b7c18e934817aea94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="a89d3-102">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="a89d3-102">Creating Prototypes in Managed Code</span></span>
<span data-ttu-id="a89d3-103">Toto téma popisuje, jak přistupovat k nespravovaným funkcím a zavádí několik polí atributů, které opatřit poznámkami definici metody ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="a89d3-103">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="a89d3-104">Příklady, které ukazují, jak vytvořit. Na základě NET deklarace, který se má použít s platformou vyvolání najdete v tématu [zařazování dat s vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="a89d3-104">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="a89d3-105">Než se dostanete k nespravované funkce knihoven DLL ze spravovaného kódu, musíte znát název funkce a název knihovny DLL, která vyexportuje ji.</span><span class="sxs-lookup"><span data-stu-id="a89d3-105">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="a89d3-106">Pomocí těchto informací můžete začít zapisovat spravované definici nespravované funkci, která je implementovaná v knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="a89d3-106">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="a89d3-107">Kromě toho můžete upravit způsob, jakým této platformě vyvolání vytvoří funkci a zařazuje dat do a z funkce.</span><span class="sxs-lookup"><span data-stu-id="a89d3-107">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a89d3-108">Funkce rozhraní API Win32, které přidělují řetězec umožňují volné řetězec pomocí metody `LocalFree`.</span><span class="sxs-lookup"><span data-stu-id="a89d3-108">Win32 API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="a89d3-109">Vyvolání platformy zpracovává tyto parametry jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="a89d3-109">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="a89d3-110">Pro platformu vyvolat volání, zkontrolujte parametr `IntPtr` zadejte místo `String` typu.</span><span class="sxs-lookup"><span data-stu-id="a89d3-110">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="a89d3-111">Pomocí metody, které jsou poskytovány <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> třídy ručně převést na řetězec typu a volné ji ručně.</span><span class="sxs-lookup"><span data-stu-id="a89d3-111">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="a89d3-112">Základy deklarace</span><span class="sxs-lookup"><span data-stu-id="a89d3-112">Declaration Basics</span></span>  
 <span data-ttu-id="a89d3-113">Spravované definice k nespravovaným funkcím jsou závislá, jak můžete vidět v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="a89d3-113">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="a89d3-114">Příklady kódu pro více dokončení, najdete v části [příklady vyvolání platformy](../../../docs/framework/interop/platform-invoke-examples.md).</span><span class="sxs-lookup"><span data-stu-id="a89d3-114">For more complete code examples, see [Platform Invoke Examples](../../../docs/framework/interop/platform-invoke-examples.md).</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
End Class  
```  
  
 <span data-ttu-id="a89d3-115">Použít <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, nebo <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> polí k [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] prohlášení, je nutné použít <xref:System.Runtime.InteropServices.DllImportAttribute> atribut místo `Declare` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a89d3-115">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> fields to a [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
   <DllImport ("user32.dll", CharSet := CharSet.Auto)> _  
   Public Shared Function MessageBox (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
   End Function  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[DllImport("user32.dll")]  
    public static extern IntPtr MessageBox(int hWnd, String text,   
                                       String caption, uint type);  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
[DllImport("user32.dll")]  
    extern "C" IntPtr MessageBox(int hWnd, String* pText,  
    String* pCaption unsigned int uType);  
```  
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="a89d3-116">Úprava definice</span><span class="sxs-lookup"><span data-stu-id="a89d3-116">Adjusting the Definition</span></span>  
 <span data-ttu-id="a89d3-117">Jestli jste nastavili, je explicitně nebo Ne, polí atributů jsou v práci definování chování spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="a89d3-117">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="a89d3-118">Vyvolání platformy pracuje podle výchozí hodnoty nastavené na různá pole, které existují jako metadata v sestavení.</span><span class="sxs-lookup"><span data-stu-id="a89d3-118">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="a89d3-119">Toto výchozí chování lze změnit úpravou hodnoty jeden nebo více polí.</span><span class="sxs-lookup"><span data-stu-id="a89d3-119">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="a89d3-120">V mnoha případech použijete <xref:System.Runtime.InteropServices.DllImportAttribute> nastavte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a89d3-120">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="a89d3-121">V následující tabulce jsou uvedené kompletní sadu atribut, který vyvolání polí, které se vztahují na platformu.</span><span class="sxs-lookup"><span data-stu-id="a89d3-121">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="a89d3-122">Pro každé pole tabulka obsahuje výchozí hodnotu a obsahuje odkazy na informace o tom, jak definovat nespravovaných funkcí knihovny DLL pomocí těchto polí.</span><span class="sxs-lookup"><span data-stu-id="a89d3-122">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="a89d3-123">Pole</span><span class="sxs-lookup"><span data-stu-id="a89d3-123">Field</span></span>|<span data-ttu-id="a89d3-124">Popis</span><span class="sxs-lookup"><span data-stu-id="a89d3-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="a89d3-125">Povolí nebo zakáže přizpůsobený mapování.</span><span class="sxs-lookup"><span data-stu-id="a89d3-125">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="a89d3-126">Určuje konvence volání pro použití v předání argumentů metoda.</span><span class="sxs-lookup"><span data-stu-id="a89d3-126">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="a89d3-127">Výchozí hodnota je `WinAPI`, která odpovídá `__stdcall` pro 32bitové platformy Intel platformy.</span><span class="sxs-lookup"><span data-stu-id="a89d3-127">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="a89d3-128">Ovládací prvky úprava názvu a způsobu, jakým řetězec argumenty by měl být zařazen do funkce.</span><span class="sxs-lookup"><span data-stu-id="a89d3-128">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="a89d3-129">Výchozí hodnota je `CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="a89d3-129">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="a89d3-130">Určuje vstupní bod knihovny DLL k volání.</span><span class="sxs-lookup"><span data-stu-id="a89d3-130">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="a89d3-131">Určuje, zda vstupní bod by měl být upraven tak, aby odpovídaly znaková sada.</span><span class="sxs-lookup"><span data-stu-id="a89d3-131">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="a89d3-132">Výchozí hodnota se liší podle programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="a89d3-132">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="a89d3-133">Určuje, zda podpis spravované metoda by měla převede na nespravované podpisu, který vrátí HRESULT a má další [out, retval] argument návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a89d3-133">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="a89d3-134">Výchozí hodnota je `true` (podpis by neměl Transformovat).</span><span class="sxs-lookup"><span data-stu-id="a89d3-134">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="a89d3-135">Umožňuje volajícímu použít `Marshal.GetLastWin32Error` funkce rozhraní API k určení, zda došlo k chybě při provádění metody.</span><span class="sxs-lookup"><span data-stu-id="a89d3-135">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="a89d3-136">V jazyce Visual Basic, výchozí hodnota je `true`; v C# a C++, výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="a89d3-136">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="a89d3-137">Ovládací prvky vyvolání výjimky na unmappable znak Unicode, která je převedena na ANSI "?" znak.</span><span class="sxs-lookup"><span data-stu-id="a89d3-137">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="a89d3-138">Podrobné referenční informace najdete v tématu <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a89d3-138">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="a89d3-139">Aspekty zabezpečení vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="a89d3-139">Platform invoke security considerations</span></span>  
 <span data-ttu-id="a89d3-140">`Assert`, `Deny`, A `PermitOnly` členy <xref:System.Security.Permissions.SecurityAction> výčtu se označují jako *zásobníku modifikátory průchodu*.</span><span class="sxs-lookup"><span data-stu-id="a89d3-140">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="a89d3-141">Tito členové jsou ignorovány, když jsou použity jako deklarativní atributy na platformě vyvolání deklarace a příkazy COM definice jazyka IDL (Interface).</span><span class="sxs-lookup"><span data-stu-id="a89d3-141">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="a89d3-142">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="a89d3-142">Platform Invoke Examples</span></span>  
 <span data-ttu-id="a89d3-143">Nespravovaného ukázky v tomto tématu ilustrují použití `RegistryPermission` atribut s modifikátory procházení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="a89d3-143">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="a89d3-144">V následujícím příkladu kódu <xref:System.Security.Permissions.SecurityAction> `Assert`, `Deny`, a `PermitOnly` modifikátory jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="a89d3-144">In the following code example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionAssert();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="a89d3-145">Ale `Demand` modifikátor v následujícím příkladu je přijmout.</span><span class="sxs-lookup"><span data-stu-id="a89d3-145">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="a89d3-146"><xref:System.Security.Permissions.SecurityAction>Modifikátory fungují správně, pokud jsou uvedeny na třídu, která obsahuje (zabalí) platformu vyvolání volání.</span><span class="sxs-lookup"><span data-stu-id="a89d3-146"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
```cpp  
      [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
public ref class PInvokeWrapper  
{  
public:  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
};  
```  
  
```csharp  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
class PInvokeWrapper  
{  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
}  
```  
  
 <span data-ttu-id="a89d3-147"><xref:System.Security.Permissions.SecurityAction>Modifikátory také fungují správně vnořené scénář, kde jsou umístěny na volající platformy vyvolat volání:</span><span class="sxs-lookup"><span data-stu-id="a89d3-147"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
```cpp  
      {  
public ref class PInvokeWrapper  
public:  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
  
    [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
};  
```  
  
```csharp  
class PInvokeScenario  
{  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionInternal();  
  
    [RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
}  
```  
  
#### <a name="com-interop-examples"></a><span data-ttu-id="a89d3-148">Příklady zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="a89d3-148">COM Interop Examples</span></span>  
 <span data-ttu-id="a89d3-149">Ukázky zprostředkovatele komunikace s objekty COM v této části ilustrují použití `RegistryPermission` atribut s modifikátory procházení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="a89d3-149">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="a89d3-150">Ignorovat následující deklarace spolupráce rozhraní COM `Assert`, `Deny`, a `PermitOnly` modifikátory, podobně jako na platformu vyvolání příklady v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="a89d3-150">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDenyStubsItf  
{  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
 <span data-ttu-id="a89d3-151">Kromě toho `Demand` modifikátor nebyla přijata ve scénářích deklarace spolupráce rozhraní modelu COM, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a89d3-151">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a89d3-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="a89d3-152">See Also</span></span>  
 [<span data-ttu-id="a89d3-153">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="a89d3-153">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="a89d3-154">Určení vstupního bodu</span><span class="sxs-lookup"><span data-stu-id="a89d3-154">Specifying an Entry Point</span></span>](../../../docs/framework/interop/specifying-an-entry-point.md)  
 [<span data-ttu-id="a89d3-155">Určení znakové sady</span><span class="sxs-lookup"><span data-stu-id="a89d3-155">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)  
 [<span data-ttu-id="a89d3-156">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="a89d3-156">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="a89d3-157">Aspekty zabezpečení vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="a89d3-157">Platform Invoke Security Considerations</span></span>](http://msdn.microsoft.com/en-us/bbcc67f7-50b5-4917-88ed-cb15470409fb)  
 [<span data-ttu-id="a89d3-158">Identifikace funkcí ve knihovnách DLL</span><span class="sxs-lookup"><span data-stu-id="a89d3-158">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [<span data-ttu-id="a89d3-159">Vytvoření třídy k umístění funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="a89d3-159">Creating a Class to Hold DLL Functions</span></span>](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)  
 [<span data-ttu-id="a89d3-160">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="a89d3-160">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
