---
title: Vytváření prototypů ve spravovaném kódu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42aa63c20e1643bc3f5377fa0ad66b63c1d4433a
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422596"
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="891d9-102">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="891d9-102">Creating Prototypes in Managed Code</span></span>
<span data-ttu-id="891d9-103">Toto téma popisuje, jak získat přístup k nespravovaným funkcím a zavádí několik polí atributů, které opatřit poznámkami definici metody ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="891d9-103">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="891d9-104">Příklady, které ukazují, jak vytvořit. Na základě NET deklarace pro použití s platformu vyvolání, naleznete v tématu [zařazování dat pomocí vyvolání platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="891d9-104">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="891d9-105">Abyste mohli nespravovanou funkci knihovny DLL ze spravovaného kódu, musíte znát název funkce a název knihovny DLL, která se exportuje.</span><span class="sxs-lookup"><span data-stu-id="891d9-105">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="891d9-106">Pomocí těchto informací můžete začít psát spravované definici pro nespravovanou funkci, která je implementována v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="891d9-106">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="891d9-107">Kromě toho můžete upravit způsob, aby voláním nespravovaného kódu vytvoří funkci a zařadí data do a z funkce.</span><span class="sxs-lookup"><span data-stu-id="891d9-107">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="891d9-108">Funkce rozhraní Windows API, které přidělit řetězec umožňují zdarma řetězec pomocí metody `LocalFree`.</span><span class="sxs-lookup"><span data-stu-id="891d9-108">Windows API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="891d9-109">Vyvolání platformy zpracovává jinak tyto parametry.</span><span class="sxs-lookup"><span data-stu-id="891d9-109">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="891d9-110">Voláními vyvolání platformy, ujistěte se, parametr `IntPtr` zadejte místo `String` typu.</span><span class="sxs-lookup"><span data-stu-id="891d9-110">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="891d9-111">Použít metody, které jsou poskytovány <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> třídy na typ ručně převést na řetězec a ručně ji zdarma.</span><span class="sxs-lookup"><span data-stu-id="891d9-111">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="891d9-112">Základní informace o deklaraci</span><span class="sxs-lookup"><span data-stu-id="891d9-112">Declaration Basics</span></span>  
 <span data-ttu-id="891d9-113">Definice spravované na nespravované funkce jsou závislá na jazyku, jak je vidět v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="891d9-113">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="891d9-114">Kompletní příklady kódu naleznete v tématu [příklady vyvolání platformy](platform-invoke-examples.md).</span><span class="sxs-lookup"><span data-stu-id="891d9-114">For more complete code examples, see [Platform Invoke Examples](platform-invoke-examples.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 <span data-ttu-id="891d9-115">Chcete-li použít <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType>, nebo <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> pole deklarace jazyka Visual Basic, musíte použít <xref:System.Runtime.InteropServices.DllImportAttribute> atribut místo `Declare` příkaz.</span><span class="sxs-lookup"><span data-stu-id="891d9-115">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> fields to a Visual Basic declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
```vb
Imports System.Runtime.InteropServices

Friend Class NativeMethods
    <DllImport("user32.dll", CharSet:=CharSet.Auto)>
    Friend Shared Function MessageBox(
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
    End Function
End Class
```
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("user32.dll")]
extern "C" int MessageBox(
    IntPtr hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="891d9-116">Úprava definice</span><span class="sxs-lookup"><span data-stu-id="891d9-116">Adjusting the Definition</span></span>  
 <span data-ttu-id="891d9-117">Ať už jste nastavili, je explicitně nebo Ne, atribut pole jsou v práci, která definuje chování spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="891d9-117">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="891d9-118">Vyvolání platformy pracuje podle výchozí hodnoty nastavené v různých polí, která jsou jako metadata do sestavení.</span><span class="sxs-lookup"><span data-stu-id="891d9-118">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="891d9-119">Toto výchozí chování můžete změnit úpravou hodnoty jednoho nebo více polí.</span><span class="sxs-lookup"><span data-stu-id="891d9-119">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="891d9-120">V mnoha případech můžete použít <xref:System.Runtime.InteropServices.DllImportAttribute> nastavit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="891d9-120">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="891d9-121">Následující tabulka uvádí kompletní sadu u atributu pole, které se vztahují na platformu vyvolání.</span><span class="sxs-lookup"><span data-stu-id="891d9-121">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="891d9-122">Pro každé pole v tabulce obsahuje výchozí hodnoty a obsahuje odkazy na informace o tom, jak použít tato pole k definování nespravovaných funkcí DLL.</span><span class="sxs-lookup"><span data-stu-id="891d9-122">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="891d9-123">Pole</span><span class="sxs-lookup"><span data-stu-id="891d9-123">Field</span></span>|<span data-ttu-id="891d9-124">Popis</span><span class="sxs-lookup"><span data-stu-id="891d9-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="891d9-125">Povolí nebo zakáže nejlepšího mapování.</span><span class="sxs-lookup"><span data-stu-id="891d9-125">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="891d9-126">Určuje konvenci volání pro použití v předávání argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="891d9-126">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="891d9-127">Výchozí hodnota je `WinAPI`, která odpovídá `__stdcall` pro 32-bit Intel podle platformy.</span><span class="sxs-lookup"><span data-stu-id="891d9-127">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="891d9-128">Ovládací prvky pozměnění názvu a způsobu, jakým řetězec argumenty by měly být zařazeny do funkce.</span><span class="sxs-lookup"><span data-stu-id="891d9-128">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="891d9-129">Výchozí hodnota je `CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="891d9-129">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="891d9-130">Určuje vstupní bod knihovny DLL, která se má volat.</span><span class="sxs-lookup"><span data-stu-id="891d9-130">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="891d9-131">Určuje, zda vstupní bod by měl být upraven tak, aby odpovídaly znakovou sadu.</span><span class="sxs-lookup"><span data-stu-id="891d9-131">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="891d9-132">Výchozí hodnota se liší podle programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="891d9-132">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="891d9-133">Určuje, zda by měl podpis spravované metody transformuje na nespravovanému podpisu, který vrací HRESULT a obsahuje další [out, retval] argument pro návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="891d9-133">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="891d9-134">Výchozí hodnota je `true` (podpis by neměl transformuje).</span><span class="sxs-lookup"><span data-stu-id="891d9-134">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="891d9-135">Umožňuje volajícímu použít `Marshal.GetLastWin32Error` – funkce rozhraní API k určení, zda došlo k chybě při provádění metody.</span><span class="sxs-lookup"><span data-stu-id="891d9-135">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="891d9-136">V jazyce Visual Basic, výchozí hodnota je `true`; v C# a C++, výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="891d9-136">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="891d9-137">Ovládací prvky vyvolání výjimky na nemapovatelný znak Unicode, který je převeden na ANSI "?" znak.</span><span class="sxs-lookup"><span data-stu-id="891d9-137">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="891d9-138">Podrobné referenční informace najdete v tématu <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="891d9-138">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="891d9-139">Důležité informace o zabezpečení vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="891d9-139">Platform invoke security considerations</span></span>  
 <span data-ttu-id="891d9-140">`Assert`, `Deny`, A `PermitOnly` členy <xref:System.Security.Permissions.SecurityAction> výčtu jsou označovány jako *modifikátory procházení zásobníku*.</span><span class="sxs-lookup"><span data-stu-id="891d9-140">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="891d9-141">Tyto členy jsou ignorovány, pokud jsou použity jako deklarativních atributů na platformě vyvolat deklarace a příkazy COM rozhraní Definition Language (IDL).</span><span class="sxs-lookup"><span data-stu-id="891d9-141">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="891d9-142">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="891d9-142">Platform Invoke Examples</span></span>  
 <span data-ttu-id="891d9-143">Nespravovaného vzorků v této části ilustrují použití `RegistryPermission` atribut modifikátory procházení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="891d9-143">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="891d9-144">V následujícím příkladu <xref:System.Security.Permissions.SecurityAction> `Assert`, `Deny`, a `PermitOnly` modifikátory jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="891d9-144">In the following example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="891d9-145">Ale `Demand` modifikátor v následujícím příkladu je přijat.</span><span class="sxs-lookup"><span data-stu-id="891d9-145">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```csharp
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="891d9-146"><xref:System.Security.Permissions.SecurityAction> Modifikátory správně fungovat, pokud jsou umístěny na třídu, která obsahuje (zabalí) platforma volání funkce invoke.</span><span class="sxs-lookup"><span data-stu-id="891d9-146"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
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
  
 <span data-ttu-id="891d9-147"><xref:System.Security.Permissions.SecurityAction> volání funkce invoke modifikátory také fungovat správně v vnořené scénář, kde jsou umístěny na volajícím platformy:</span><span class="sxs-lookup"><span data-stu-id="891d9-147"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
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
  
#### <a name="com-interop-examples"></a><span data-ttu-id="891d9-148">Příklady vzájemné spolupráce COM</span><span class="sxs-lookup"><span data-stu-id="891d9-148">COM Interop Examples</span></span>  
 <span data-ttu-id="891d9-149">COM interop vzorků v této části ilustrují použití `RegistryPermission` atribut modifikátory procházení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="891d9-149">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="891d9-150">Ignorovat následující deklarace vzájemné spolupráce rozhraní modelu COM `Assert`, `Deny`, a `PermitOnly` modifikátory, podobně jako na platformu vyvolání příklady v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="891d9-150">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
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
  
 <span data-ttu-id="891d9-151">Kromě toho `Demand` modifikátor nebyla přijata ve scénářích deklarace vzájemné spolupráce rozhraní modelu COM, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="891d9-151">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="891d9-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="891d9-152">See also</span></span>

- [<span data-ttu-id="891d9-153">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="891d9-153">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="891d9-154">Určení vstupního bodu</span><span class="sxs-lookup"><span data-stu-id="891d9-154">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="891d9-155">Určení znakové sady</span><span class="sxs-lookup"><span data-stu-id="891d9-155">Specifying a Character Set</span></span>](specifying-a-character-set.md)
- [<span data-ttu-id="891d9-156">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="891d9-156">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- <span data-ttu-id="891d9-157">[Důležité informace o zabezpečení vyvolání platformy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="891d9-157">[Platform Invoke Security Considerations](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span></span>
- [<span data-ttu-id="891d9-158">Identifikace funkcí ve knihovnách DLL</span><span class="sxs-lookup"><span data-stu-id="891d9-158">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="891d9-159">Vytvoření třídy k umístění funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="891d9-159">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="891d9-160">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="891d9-160">Calling a DLL Function</span></span>](calling-a-dll-function.md)
