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
ms.openlocfilehash: 712040c3482b51c4dafe0ee87fdda8cd848fb7fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123617"
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="30b23-102">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="30b23-102">Creating Prototypes in Managed Code</span></span>
<span data-ttu-id="30b23-103">Toto téma popisuje, jak získat přístup k nespravovaným funkcím a zavádí několik polí atributů, která přistupují k definici metody ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="30b23-103">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="30b23-104">Příklady, které ukazují, jak vytvořit. Deklarace založené na síti, které se mají použít s voláním platformy, najdete v tématu [zařazování dat pomocí vyvolání platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="30b23-104">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="30b23-105">Předtím, než budete moci získat přístup k nespravované funkci knihovny DLL ze spravovaného kódu, je nutné znát název funkce a název knihovny DLL, která ji exportuje.</span><span class="sxs-lookup"><span data-stu-id="30b23-105">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="30b23-106">Pomocí těchto informací můžete začít psát spravovanou definici pro nespravovanou funkci, která je implementována v knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="30b23-106">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="30b23-107">Kromě toho můžete upravit způsob, jakým volání platformy vytvoří funkci a zařadí data do a z funkce.</span><span class="sxs-lookup"><span data-stu-id="30b23-107">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30b23-108">Funkce rozhraní API systému Windows, které přidělují řetězec, umožňují uvolnit řetězec pomocí metody, jako je `LocalFree`například.</span><span class="sxs-lookup"><span data-stu-id="30b23-108">Windows API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="30b23-109">Volání platformy zpracovává tyto parametry odlišně.</span><span class="sxs-lookup"><span data-stu-id="30b23-109">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="30b23-110">Pro volání vyvolání platformy nastavte parametr jako `IntPtr` typ místo `String` typu.</span><span class="sxs-lookup"><span data-stu-id="30b23-110">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="30b23-111">Použijte metody, které jsou k dispozici v <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> třídě, a převeďte typ na řetězec ručně a uvolněte ho ručně.</span><span class="sxs-lookup"><span data-stu-id="30b23-111">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="30b23-112">Základy deklarace</span><span class="sxs-lookup"><span data-stu-id="30b23-112">Declaration Basics</span></span>  
 <span data-ttu-id="30b23-113">Spravované definice na nespravované funkce jsou závislé na jazyku, jak vidíte v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="30b23-113">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="30b23-114">Další kompletní příklady kódu naleznete v tématu [Příklady vyvolání platformy](platform-invoke-examples.md).</span><span class="sxs-lookup"><span data-stu-id="30b23-114">For more complete code examples, see [Platform Invoke Examples](platform-invoke-examples.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 <span data-ttu-id="30b23-115">Chcete-li <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>použít <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>pole <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType>,, <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> , nebo na deklaraci Visual Basic, je nutné použít <xref:System.Runtime.InteropServices.DllImportAttribute> atribut namísto `Declare` příkazu.</span><span class="sxs-lookup"><span data-stu-id="30b23-115">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> fields to a Visual Basic declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
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
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="30b23-116">Úprava definice</span><span class="sxs-lookup"><span data-stu-id="30b23-116">Adjusting the Definition</span></span>  
 <span data-ttu-id="30b23-117">Bez ohledu na to, jestli jste je explicitně nastavili, jsou pole atributu v práci, která definují chování spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="30b23-117">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="30b23-118">Vyvolání platformy funguje v závislosti na výchozích hodnotách, které jsou nastaveny v různých polích, která existují jako metadata v sestavení.</span><span class="sxs-lookup"><span data-stu-id="30b23-118">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="30b23-119">Toto výchozí chování můžete změnit úpravou hodnot jednoho nebo více polí.</span><span class="sxs-lookup"><span data-stu-id="30b23-119">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="30b23-120">V mnoha případech můžete použít <xref:System.Runtime.InteropServices.DllImportAttribute> k nastavení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="30b23-120">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="30b23-121">V následující tabulce je uvedena kompletní sada polí atributů, která se vztahují k vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="30b23-121">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="30b23-122">Pro každé pole tabulka obsahuje výchozí hodnotu a odkaz na informace o tom, jak tato pole použít k definování nespravovaných funkcí knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="30b23-122">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="30b23-123">Pole</span><span class="sxs-lookup"><span data-stu-id="30b23-123">Field</span></span>|<span data-ttu-id="30b23-124">Popis</span><span class="sxs-lookup"><span data-stu-id="30b23-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="30b23-125">Povolí nebo zakáže mapování podle nejlepšího umístění.</span><span class="sxs-lookup"><span data-stu-id="30b23-125">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="30b23-126">Určuje konvenci volání, která se má použít při předávání argumentů metody.</span><span class="sxs-lookup"><span data-stu-id="30b23-126">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="30b23-127">Výchozí hodnota je `WinAPI`, která odpovídá `__stdcall` 32 platformám založeným na technologii Intel.</span><span class="sxs-lookup"><span data-stu-id="30b23-127">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="30b23-128">Ovládací prvky pro pokládání názvů a způsob, jakým se mají zařazovat řetězcové argumenty do funkce.</span><span class="sxs-lookup"><span data-stu-id="30b23-128">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="30b23-129">Výchozí formát je `CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="30b23-129">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="30b23-130">Určuje vstupní bod knihovny DLL, který má být volán.</span><span class="sxs-lookup"><span data-stu-id="30b23-130">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="30b23-131">Určuje, zda má být vstupní bod změněn tak, aby odpovídal znakové sadě.</span><span class="sxs-lookup"><span data-stu-id="30b23-131">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="30b23-132">Výchozí hodnota se liší podle programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="30b23-132">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="30b23-133">Určuje, zda má být podpis spravované metody transformován na nespravovaný podpis, který vrací HRESULT a má další argument [out, retval] pro návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="30b23-133">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="30b23-134">Výchozí hodnota je `true` (podpis by neměl být transformované).</span><span class="sxs-lookup"><span data-stu-id="30b23-134">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="30b23-135">Umožňuje volajícímu použít funkci `Marshal.GetLastWin32Error` rozhraní API k určení, zda došlo k chybě při provádění metody.</span><span class="sxs-lookup"><span data-stu-id="30b23-135">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="30b23-136">V Visual Basic je `true`výchozí hodnota; v jazyce C# a C++ je `false`výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="30b23-136">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="30b23-137">Řídí vyvolání výjimky na nemapovatelný znak Unicode, který je převeden na znak ANSI "?".</span><span class="sxs-lookup"><span data-stu-id="30b23-137">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="30b23-138">Podrobné referenční informace najdete v tématu <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="30b23-138">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="30b23-139">Požadavky na zabezpečení volání platformy</span><span class="sxs-lookup"><span data-stu-id="30b23-139">Platform invoke security considerations</span></span>  
 <span data-ttu-id="30b23-140">Členy `Assert` <xref:System.Security.Permissions.SecurityAction> , `Deny`a `PermitOnly` jsou označováni jako *modifikátory procházení zásobníku*.</span><span class="sxs-lookup"><span data-stu-id="30b23-140">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="30b23-141">Tyto členy jsou ignorovány, pokud jsou používány jako deklarativní atributy v deklaracích vyvolání platformy a příkazy IDL (Interface Definition Language) modelu COM.</span><span class="sxs-lookup"><span data-stu-id="30b23-141">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="30b23-142">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="30b23-142">Platform Invoke Examples</span></span>  
 <span data-ttu-id="30b23-143">Ukázky pro volání platformy v této části ilustrují použití `RegistryPermission` atributu s modifikátory procházení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="30b23-143">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="30b23-144">V <xref:System.Security.Permissions.SecurityAction> `Assert`následujícím příkladu jsou modifikátory, `Deny`a `PermitOnly` ignorovány.</span><span class="sxs-lookup"><span data-stu-id="30b23-144">In the following example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
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
  
 <span data-ttu-id="30b23-145">Nicméně `Demand` modifikátor v následujícím příkladu je přijat.</span><span class="sxs-lookup"><span data-stu-id="30b23-145">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```csharp
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="30b23-146"><xref:System.Security.Permissions.SecurityAction>modifikátory fungují správně, pokud jsou umístěny na třídu, která obsahuje (zabalí) volání vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="30b23-146"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
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
  
 <span data-ttu-id="30b23-147"><xref:System.Security.Permissions.SecurityAction>modifikátory fungují správně i ve vnořeném scénáři, kde jsou umístěny na volajícím volání vyvolání platformy:</span><span class="sxs-lookup"><span data-stu-id="30b23-147"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
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
  
#### <a name="com-interop-examples"></a><span data-ttu-id="30b23-148">Příklady spolupráce modelu COM</span><span class="sxs-lookup"><span data-stu-id="30b23-148">COM Interop Examples</span></span>  
 <span data-ttu-id="30b23-149">Ukázky spolupráce modelu COM v této části ilustrují použití `RegistryPermission` atributu s modifikátory procházení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="30b23-149">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="30b23-150">Následující deklarace rozhraní COM interop rozhraní ignorují `Assert`modifikátory `Deny`, `PermitOnly` a podobně jako příklady vyvolání platformy v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="30b23-150">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="30b23-151">Kromě toho `Demand` modifikátor není přijat ve scénářích deklarace rozhraní Interop modelu COM, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="30b23-151">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
```csharp  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="30b23-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="30b23-152">See also</span></span>

- [<span data-ttu-id="30b23-153">Používání nespravovaných funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="30b23-153">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="30b23-154">Určení vstupního bodu</span><span class="sxs-lookup"><span data-stu-id="30b23-154">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="30b23-155">Určení sady znaků</span><span class="sxs-lookup"><span data-stu-id="30b23-155">Specifying a Character Set</span></span>](specifying-a-character-set.md)
- [<span data-ttu-id="30b23-156">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="30b23-156">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- <span data-ttu-id="30b23-157">[Požadavky na zabezpečení volání platformy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="30b23-157">[Platform Invoke Security Considerations](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span></span>
- [<span data-ttu-id="30b23-158">Identifikace funkcí ve knihovnách DLL</span><span class="sxs-lookup"><span data-stu-id="30b23-158">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="30b23-159">Vytvoření třídy k umístění funkcí DLL</span><span class="sxs-lookup"><span data-stu-id="30b23-159">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="30b23-160">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="30b23-160">Calling a DLL Function</span></span>](calling-a-dll-function.md)
