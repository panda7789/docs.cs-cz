---
title: "Předávání struktur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a30905fdcf7063f6ecdae0346c9c5ee39b450be9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="passing-structures"></a>Předávání struktur
Mnoho nespravovaných funkcí předpokládá, že předat jako parametr pro funkci, členové struktury (uživatelem definované typy v jazyce Visual Basic) nebo členy třídy, které jsou definovány ve spravovaném kódu. Při předávání struktur nebo třídy do nespravovaného kódu pomocí platformy vyvolání, je třeba zadat další informace a zachovat původní rozložení a zarovnání. Toto téma představuje <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut, který používáte k definování formátovaný typy. Pro spravované struktury a třídy, můžete vybrat z několika předvídatelný rozložení chování poskytl **LayoutKind** výčtu.  
  
 Z centrální na pojmy uvedené v tomto tématu je důležitý rozdíl mezi typy struktury a třídy. Typy hodnot jsou struktury a třídy odkazové typy – třídy vždycky poskytovat alespoň jednu úroveň dereference paměti (ukazatel na hodnotu). Tento rozdíl je důležité, protože nespravované funkce často potřebují indirection, jak ukazují podpisů v první sloupec v následující tabulce. Spravované struktura a deklarace tříd v zbývající sloupce ukazují na úroveň, do kterého můžete upravit úroveň dereference v vaší deklaraci. Deklarace jsou uvedené pro Visual Basic a Visual C#.  
  
|Nespravované podpis|Spravované deklarace: <br />žádné indirection<br />`Structure MyType`<br />`struct MyType;`|Spravované deklarace: <br />jedna úroveň dereference<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Požadavky na nula úrovně dereference.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Přidá nulové úrovně dereference.|Není možné, protože je již jedna úroveň dereference.|  
|`DoWork(MyType* x);`<br /><br /> Vyžaduje jednu úroveň dereference.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Přidá jednu úroveň dereference.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Přidá nulové úrovně dereference.|  
|`DoWork(MyType** x);`<br /><br /> Vyžaduje dvě úrovně dereference.|Není možné, protože **ByRef** **ByRef** nebo `ref` `ref` nelze použít.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Přidá jednu úroveň dereference.|  
  
 V tabulce jsou popsány následující pokyny pro deklarace volání nespravovaného kódu:  
  
-   Použijte strukturu předaná hodnota když nespravované funkce požaduje žádné indirection.  
  
-   Použijte strukturou předaná odkaz nebo třídu předaná hodnota při nespravované funkce vyžaduje jednu úroveň dereference.  
  
-   Použití třídy předaná odkaz při nespravované funkce vyžaduje dvě úrovně dereference.  
  
## <a name="declaring-and-passing-structures"></a>Deklarace a předáním struktury  
 Následující příklad ukazuje, jak definovat `Point` a `Rect` struktury v spravovaného kódu a předejte typy jako parametr **PtInRect** funkce v souboru User32.dll. **PtInRect** má následující nespravované podpis:  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Všimněte si, že je nutné předat Rect – struktura odkazem, vzhledem k tomu, že funkce očekává ukazatel typu Rect –.  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Class Win32API      
    Declare Auto Function PtInRect Lib "user32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
    public int x;  
    public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
    [FieldOffset(0)] public int left;  
    [FieldOffset(4)] public int top;  
    [FieldOffset(8)] public int right;  
    [FieldOffset(12)] public int bottom;  
}     
  
class Win32API {  
    [DllImport("User32.dll")]  
    public static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a>Deklarace a předávání tříd  
 Členy třídy můžete předat do nespravované funkce knihovny DLL, dokud třída obsahuje člen pevné rozložení. Následující příklad ukazuje, jak předat členy `MySystemTime` třída, která jsou definována v sekvenčním pořadí, na **GetSystemTime** v souboru User32.dll. **GetSystemTime** má následující nespravované podpis:  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Na rozdíl od typy hodnot třídy mají vždy alespoň jedna úroveň dereference.  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
Imports Microsoft.VisualBasic  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short   
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Public Class Win32  
    Declare Auto Sub GetSystemTime Lib "Kernel32.dll"(sysTime _  
        As MySystemTime)  
    Declare Auto Function MessageBox Lib "User32.dll"(hWnd As IntPtr, _  
        txt As String, caption As String, Typ As Integer) As Integer  
End Class  
  
Public Class TestPlatformInvoke      
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        Win32.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        Win32.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)        
    End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;   
    public ushort wMonth;  
    public ushort wDayOfWeek;   
    public ushort wDay;   
    public ushort wHour;   
    public ushort wMinute;   
    public ushort wSecond;   
    public ushort wMilliseconds;   
}  
class Win32API {  
    [DllImport("Kernel32.dll")]  
    public static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet=CharSet.Auto)]  
     public static extern int MessageBox(IntPtr hWnd,  
         string text, string caption, int options);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        Win32API.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        Win32API.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md)  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
