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
ms.openlocfilehash: c65634a1046b193d500e505d945784504285f93a
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412328"
---
# <a name="creating-prototypes-in-managed-code"></a>Vytváření prototypů ve spravovaném kódu
Toto téma popisuje, jak získat přístup k nespravovaným funkcím a zavádí několik polí atributů, které opatřit poznámkami definici metody ve spravovaném kódu. Příklady, které ukazují, jak vytvořit. Na základě NET deklarace pro použití s platformu vyvolání, naleznete v tématu [zařazování dat pomocí vyvolání platformy](marshaling-data-with-platform-invoke.md).  
  
 Abyste mohli nespravovanou funkci knihovny DLL ze spravovaného kódu, musíte znát název funkce a název knihovny DLL, která se exportuje. Pomocí těchto informací můžete začít psát spravované definici pro nespravovanou funkci, která je implementována v knihovně DLL. Kromě toho můžete upravit způsob, aby voláním nespravovaného kódu vytvoří funkci a zařadí data do a z funkce.  
  
> [!NOTE]
>  Funkce rozhraní Windows API, které přidělit řetězec umožňují zdarma řetězec pomocí metody `LocalFree`. Vyvolání platformy zpracovává jinak tyto parametry. Voláními vyvolání platformy, ujistěte se, parametr `IntPtr` zadejte místo `String` typu. Použít metody, které jsou poskytovány <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> třídy na typ ručně převést na řetězec a ručně ji zdarma.  
  
## <a name="declaration-basics"></a>Základní informace o deklaraci  
 Definice spravované na nespravované funkce jsou závislá na jazyku, jak je vidět v následujícím příkladu. Kompletní příklady kódu naleznete v tématu [příklady vyvolání platformy](platform-invoke-examples.md).  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 Použít <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, nebo <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> polím [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] prohlášení, je nutné použít <xref:System.Runtime.InteropServices.DllImportAttribute> atribut místo `Declare` příkazu.  
  
```vb
Imports System
Imports System.Runtime.InteropServices

Friend Class WindowsAPI
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

internal static class WindowsAPI
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
 Ať už jste nastavili, je explicitně nebo Ne, atribut pole jsou v práci, která definuje chování spravovaného kódu. Vyvolání platformy pracuje podle výchozí hodnoty nastavené v různých polí, která jsou jako metadata do sestavení. Toto výchozí chování můžete změnit úpravou hodnoty jednoho nebo více polí. V mnoha případech můžete použít <xref:System.Runtime.InteropServices.DllImportAttribute> nastavit hodnotu.  
  
 Následující tabulka uvádí kompletní sadu u atributu pole, které se vztahují na platformu vyvolání. Pro každé pole v tabulce obsahuje výchozí hodnoty a obsahuje odkazy na informace o tom, jak použít tato pole k definování nespravovaných funkcí DLL.  
  
|Pole|Popis|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|Povolí nebo zakáže nejlepšího mapování.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|Určuje konvenci volání pro použití v předávání argumentů metody. Výchozí hodnota je `WinAPI`, která odpovídá `__stdcall` pro 32-bit Intel podle platformy.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|Ovládací prvky pozměnění názvu a způsobu, jakým řetězec argumenty by měly být zařazeny do funkce. Výchozí hodnota je `CharSet.Ansi`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|Určuje vstupní bod knihovny DLL, která se má volat.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|Určuje, zda vstupní bod by měl být upraven tak, aby odpovídaly znakovou sadu. Výchozí hodnota se liší podle programovacího jazyka.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|Určuje, zda by měl podpis spravované metody transformuje na nespravovanému podpisu, který vrací HRESULT a obsahuje další [out, retval] argument pro návratovou hodnotu.<br /><br /> Výchozí hodnota je `true` (podpis by neměl transformuje).|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|Umožňuje volajícímu použít `Marshal.GetLastWin32Error` – funkce rozhraní API k určení, zda došlo k chybě při provádění metody. V jazyce Visual Basic, výchozí hodnota je `true`; v C# a C++, výchozí hodnota je `false`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|Ovládací prvky vyvolání výjimky na nemapovatelný znak Unicode, který je převeden na ANSI "?" znak.|  
  
 Podrobné referenční informace najdete v tématu <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
## <a name="platform-invoke-security-considerations"></a>Důležité informace o zabezpečení vyvolání platformy  
 `Assert`, `Deny`, A `PermitOnly` členy <xref:System.Security.Permissions.SecurityAction> výčtu jsou označovány jako *modifikátory procházení zásobníku*. Tyto členy jsou ignorovány, pokud jsou použity jako deklarativních atributů na platformě vyvolat deklarace a příkazy COM rozhraní Definition Language (IDL).  
  
### <a name="platform-invoke-examples"></a>Příklady vyvolání platformy  
 Nespravovaného vzorků v této části ilustrují použití `RegistryPermission` atribut modifikátory procházení zásobníku.  
  
 V následujícím příkladu kódu <xref:System.Security.Permissions.SecurityAction> `Assert`, `Deny`, a `PermitOnly` modifikátory jsou ignorovány.  
  
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
  
 Ale `Demand` modifikátor v následujícím příkladu je přijat.  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <xref:System.Security.Permissions.SecurityAction> Modifikátory správně fungovat, pokud jsou umístěny na třídu, která obsahuje (zabalí) platforma volání funkce invoke.  
  
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
  
 <xref:System.Security.Permissions.SecurityAction> volání funkce invoke modifikátory také fungovat správně v vnořené scénář, kde jsou umístěny na volajícím platformy:  
  
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
  
#### <a name="com-interop-examples"></a>Příklady vzájemné spolupráce COM  
 COM interop vzorků v této části ilustrují použití `RegistryPermission` atribut modifikátory procházení zásobníku.  
  
 Ignorovat následující deklarace vzájemné spolupráce rozhraní modelu COM `Assert`, `Deny`, a `PermitOnly` modifikátory, podobně jako na platformu vyvolání příklady v předchozí části.  
  
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
  
 Kromě toho `Demand` modifikátor nebyla přijata ve scénářích deklarace vzájemné spolupráce rozhraní modelu COM, jak je znázorněno v následujícím příkladu.  
  
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
  
## <a name="see-also"></a>Viz také:
- [Používání nespravovaných funkcí DLL](consuming-unmanaged-dll-functions.md)
- [Určení vstupního bodu](specifying-an-entry-point.md)
- [Určení znakové sady](specifying-a-character-set.md)
- [Příklady vyvolání platformy](platform-invoke-examples.md)
- [Důležité informace o zabezpečení vyvolání platformy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))
- [Identifikace funkcí ve knihovnách DLL](identifying-functions-in-dlls.md)
- [Vytvoření třídy k umístění funkcí DLL](creating-a-class-to-hold-dll-functions.md)
- [Volání funkce DLL](calling-a-dll-function.md)
