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
# <a name="creating-prototypes-in-managed-code"></a>Vytváření prototypů ve spravovaném kódu
Toto téma popisuje, jak získat přístup k nespravovaným funkcím a zavádí několik polí atributů, která přistupují k definici metody ve spravovaném kódu. Příklady, které ukazují, jak vytvořit. Deklarace založené na síti, které se mají použít s voláním platformy, najdete v tématu [zařazování dat pomocí vyvolání platformy](marshaling-data-with-platform-invoke.md).  
  
 Předtím, než budete moci získat přístup k nespravované funkci knihovny DLL ze spravovaného kódu, je nutné znát název funkce a název knihovny DLL, která ji exportuje. Pomocí těchto informací můžete začít psát spravovanou definici pro nespravovanou funkci, která je implementována v knihovně DLL. Kromě toho můžete upravit způsob, jakým volání platformy vytvoří funkci a zařadí data do a z funkce.  
  
> [!NOTE]
> Funkce rozhraní API systému Windows, které přidělují řetězec, umožňují uvolnit řetězec pomocí metody, jako je například `LocalFree`. Volání platformy zpracovává tyto parametry odlišně. Pro volání vyvolání platformy nastavte parametr `IntPtr` typ místo `String` typu. Použijte metody, které jsou k dispozici třídou <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> k převedení typu na řetězec ručně a jeho uvolnění ručně.  
  
## <a name="declaration-basics"></a>Základy deklarace  
 Spravované definice na nespravované funkce jsou závislé na jazyku, jak vidíte v následujících příkladech. Další kompletní příklady kódu naleznete v tématu [Příklady vyvolání platformy](platform-invoke-examples.md).  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 Chcete-li použít pole <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType>nebo <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> k deklaraci Visual Basic, je nutné použít atribut <xref:System.Runtime.InteropServices.DllImportAttribute> namísto příkazu `Declare`.  
  
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
  
## <a name="adjusting-the-definition"></a>Úprava definice  
 Bez ohledu na to, jestli jste je explicitně nastavili, jsou pole atributu v práci, která definují chování spravovaného kódu. Vyvolání platformy funguje v závislosti na výchozích hodnotách, které jsou nastaveny v různých polích, která existují jako metadata v sestavení. Toto výchozí chování můžete změnit úpravou hodnot jednoho nebo více polí. V mnoha případech použijete <xref:System.Runtime.InteropServices.DllImportAttribute> k nastavení hodnoty.  
  
 V následující tabulce je uvedena kompletní sada polí atributů, která se vztahují k vyvolání platformy. Pro každé pole tabulka obsahuje výchozí hodnotu a odkaz na informace o tom, jak tato pole použít k definování nespravovaných funkcí knihovny DLL.  
  
|Pole|Popis|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|Povolí nebo zakáže mapování podle nejlepšího umístění.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|Určuje konvenci volání, která se má použít při předávání argumentů metody. Výchozí hodnota je `WinAPI`, která odpovídá `__stdcall`ám 32 platforem založených na platformě Intel.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|Ovládací prvky pro pokládání názvů a způsob, jakým se mají zařazovat řetězcové argumenty do funkce. Výchozí hodnota je `CharSet.Ansi`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|Určuje vstupní bod knihovny DLL, který má být volán.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|Určuje, zda má být vstupní bod změněn tak, aby odpovídal znakové sadě. Výchozí hodnota se liší podle programovacího jazyka.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|Určuje, zda má být podpis spravované metody transformován na nespravovaný podpis, který vrací HRESULT a má další argument [out, retval] pro návratovou hodnotu.<br /><br /> Výchozí hodnota je `true` (podpis by neměl být transformované).|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|Umožňuje volajícímu použít funkci rozhraní `Marshal.GetLastWin32Error` API k určení, zda došlo k chybě při provádění metody. V Visual Basic je výchozí hodnota `true`; v C# a C++je výchozí hodnota `false`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|Řídí vyvolání výjimky na nemapovatelný znak Unicode, který je převeden na znak ANSI "?".|  
  
 Podrobné referenční informace najdete v tématu <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
## <a name="platform-invoke-security-considerations"></a>Požadavky na zabezpečení volání platformy  
 `Assert`, `Deny`a `PermitOnly` členů <xref:System.Security.Permissions.SecurityAction> výčtu se označují jako *modifikátory procházení zásobníku*. Tyto členy jsou ignorovány, pokud jsou používány jako deklarativní atributy v deklaracích vyvolání platformy a příkazy IDL (Interface Definition Language) modelu COM.  
  
### <a name="platform-invoke-examples"></a>Příklady vyvolání platformy  
 Ukázky pro volání platformy v této části ilustrují použití atributu `RegistryPermission` s modifikátory procházení zásobníku.  
  
 V následujícím příkladu se <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`a modifikátory `PermitOnly` ignorují.  
  
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
  
 Nicméně modifikátor `Demand` v následujícím příkladu je přijat.  
  
```csharp
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <xref:System.Security.Permissions.SecurityAction> modifikátory fungují správně, pokud jsou umístěny na třídu, která obsahuje (zabalí) volání vyvolání platformy.  
  
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
  
 <xref:System.Security.Permissions.SecurityAction> modifikátory fungují správně ve vnořeném scénáři, kde jsou umístěny na volajícím volání vyvolání platformy:  
  
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
  
#### <a name="com-interop-examples"></a>Příklady spolupráce modelu COM  
 Ukázky spolupráce modelu COM v této části ilustrují použití atributu `RegistryPermission` s modifikátory procházení zásobníku.  
  
 Následující deklarace rozhraní COM interop rozhraní ignorují modifikátory `Assert`, `Deny`a `PermitOnly` podobně jako příklady vyvolání platformy v předchozí části.  
  
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
  
 Kromě toho modifikátor `Demand` není přijat ve scénářích deklarace rozhraní Interop modelu COM, jak je znázorněno v následujícím příkladu.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Používání nespravovaných funkcí DLL](consuming-unmanaged-dll-functions.md)
- [Určení vstupního bodu](specifying-an-entry-point.md)
- [Určení znakové sady](specifying-a-character-set.md)
- [Příklady vyvolání platformy](platform-invoke-examples.md)
- [Požadavky na zabezpečení volání platformy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))
- [Identifikace funkcí ve knihovnách DLL](identifying-functions-in-dlls.md)
- [Vytvoření třídy k umístění funkcí DLL](creating-a-class-to-hold-dll-functions.md)
- [Volání funkce DLL](calling-a-dll-function.md)
