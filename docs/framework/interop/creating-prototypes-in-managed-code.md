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
ms.openlocfilehash: b305158ac87f01044bae5455cea07ca3b3a2e491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="creating-prototypes-in-managed-code"></a>Vytváření prototypů ve spravovaném kódu
Toto téma popisuje, jak přistupovat k nespravovaným funkcím a zavádí několik polí atributů, které opatřit poznámkami definici metody ve spravovaném kódu. Příklady, které ukazují, jak vytvořit. Na základě NET deklarace, který se má použít s platformou vyvolání najdete v tématu [zařazování dat s vyvolání platformy](marshaling-data-with-platform-invoke.md).  
  
 Než se dostanete k nespravované funkce knihoven DLL ze spravovaného kódu, musíte znát název funkce a název knihovny DLL, která vyexportuje ji. Pomocí těchto informací můžete začít zapisovat spravované definici nespravované funkci, která je implementovaná v knihovny DLL. Kromě toho můžete upravit způsob, jakým této platformě vyvolání vytvoří funkci a zařazuje dat do a z funkce.  
  
> [!NOTE]
>  Funkce rozhraní API Win32, které přidělují řetězec umožňují volné řetězec pomocí metody `LocalFree`. Vyvolání platformy zpracovává tyto parametry jiným způsobem. Pro platformu vyvolat volání, zkontrolujte parametr `IntPtr` zadejte místo `String` typu. Pomocí metody, které jsou poskytovány <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> třídy ručně převést na řetězec typu a volné ji ručně.  
  
## <a name="declaration-basics"></a>Základy deklarace  
 Spravované definice k nespravovaným funkcím jsou závislá, jak můžete vidět v následujících příkladech. Příklady kódu pro více dokončení, najdete v části [příklady vyvolání platformy](platform-invoke-examples.md).  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
End Class  
```  
  
 Použít <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, nebo <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> polí k [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] prohlášení, je nutné použít <xref:System.Runtime.InteropServices.DllImportAttribute> atribut místo `Declare` příkaz.  
  
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
  
## <a name="adjusting-the-definition"></a>Úprava definice  
 Jestli jste nastavili, je explicitně nebo Ne, polí atributů jsou v práci definování chování spravovaného kódu. Vyvolání platformy pracuje podle výchozí hodnoty nastavené na různá pole, které existují jako metadata v sestavení. Toto výchozí chování lze změnit úpravou hodnoty jeden nebo více polí. V mnoha případech použijete <xref:System.Runtime.InteropServices.DllImportAttribute> nastavte hodnotu.  
  
 V následující tabulce jsou uvedené kompletní sadu atribut, který vyvolání polí, které se vztahují na platformu. Pro každé pole tabulka obsahuje výchozí hodnotu a obsahuje odkazy na informace o tom, jak definovat nespravovaných funkcí knihovny DLL pomocí těchto polí.  
  
|Pole|Popis|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|Povolí nebo zakáže přizpůsobený mapování.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|Určuje konvence volání pro použití v předání argumentů metoda. Výchozí hodnota je `WinAPI`, která odpovídá `__stdcall` pro 32bitové platformy Intel platformy.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|Ovládací prvky úprava názvu a způsobu, jakým řetězec argumenty by měl být zařazen do funkce. Výchozí hodnota je `CharSet.Ansi`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|Určuje vstupní bod knihovny DLL k volání.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|Určuje, zda vstupní bod by měl být upraven tak, aby odpovídaly znaková sada. Výchozí hodnota se liší podle programovací jazyk.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|Určuje, zda podpis spravované metoda by měla převede na nespravované podpisu, který vrátí HRESULT a má další [out, retval] argument návratovou hodnotu.<br /><br /> Výchozí hodnota je `true` (podpis by neměl Transformovat).|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|Umožňuje volajícímu použít `Marshal.GetLastWin32Error` funkce rozhraní API k určení, zda došlo k chybě při provádění metody. V jazyce Visual Basic, výchozí hodnota je `true`; v C# a C++, výchozí hodnota je `false`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|Ovládací prvky vyvolání výjimky na unmappable znak Unicode, která je převedena na ANSI "?" znak.|  
  
 Podrobné referenční informace najdete v tématu <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
## <a name="platform-invoke-security-considerations"></a>Aspekty zabezpečení vyvolání platformy  
 `Assert`, `Deny`, A `PermitOnly` členy <xref:System.Security.Permissions.SecurityAction> výčtu se označují jako *zásobníku modifikátory průchodu*. Tito členové jsou ignorovány, když jsou použity jako deklarativní atributy na platformě vyvolání deklarace a příkazy COM definice jazyka IDL (Interface).  
  
### <a name="platform-invoke-examples"></a>Příklady vyvolání platformy  
 Nespravovaného ukázky v tomto tématu ilustrují použití `RegistryPermission` atribut s modifikátory procházení zásobníku.  
  
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
  
 Ale `Demand` modifikátor v následujícím příkladu je přijmout.  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <xref:System.Security.Permissions.SecurityAction> Modifikátory fungují správně, pokud jsou uvedeny na třídu, která obsahuje (zabalí) platformu vyvolání volání.  
  
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
  
 <xref:System.Security.Permissions.SecurityAction> Modifikátory také fungují správně vnořené scénář, kde jsou umístěny na volající platformy vyvolat volání:  
  
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
  
#### <a name="com-interop-examples"></a>Příklady zprostředkovatele komunikace s objekty COM  
 Ukázky zprostředkovatele komunikace s objekty COM v této části ilustrují použití `RegistryPermission` atribut s modifikátory procházení zásobníku.  
  
 Ignorovat následující deklarace spolupráce rozhraní COM `Assert`, `Deny`, a `PermitOnly` modifikátory, podobně jako na platformu vyvolání příklady v předchozí části.  
  
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
  
 Kromě toho `Demand` modifikátor nebyla přijata ve scénářích deklarace spolupráce rozhraní modelu COM, jak je znázorněno v následujícím příkladu.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Používání nespravovaných funkcí DLL](consuming-unmanaged-dll-functions.md)  
 [Určení vstupního bodu](specifying-an-entry-point.md)  
 [Určení znakové sady](specifying-a-character-set.md)  
 [Příklady vyvolání platformy](platform-invoke-examples.md)  
 [Aspekty zabezpečení vyvolání platformy](https://msdn.microsoft.com/library/bbcc67f7-50b5-4917-88ed-cb15470409fb(v=vs.100))  
 [Identifikace funkcí ve knihovnách DLL](identifying-functions-in-dlls.md)  
 [Vytvoření třídy k umístění funkcí DLL](creating-a-class-to-hold-dll-functions.md)  
 [Volání funkce DLL](calling-a-dll-function.md)
