---
title: Předávání struktur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1617a082a6ad46023add2d2df7de2561e2815881
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409689"
---
# <a name="passing-structures"></a>Předávání struktur
Mnoho nespravovaných funkcí očekávat předat jako parametr pro funkci, členové struktur (uživatelem definované typy v jazyce Visual Basic) nebo členy třídy, které jsou definovány ve spravovaném kódu. Při předávání struktur nebo tříd do nespravovaného kódu pomocí platformy vyvolat, je třeba zadat další informace a zachovat původní rozložení a zarovnání. Toto téma představuje <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut, který slouží k definování formátovaný typy. Pro spravované struktur a tříd, můžete vybrat z několika chování předvídatelné rozložení poskytnutých **LayoutKind** výčtu.  
  
 Z centrální na koncepty v tomto tématu je důležitý rozdíl mezi typy struktury a třídy. Struktury jsou typy hodnot a třídy jsou odkazové typy – třídy poskytují vždy alespoň jednu úroveň dereference paměti (ukazatel na hodnotu). Tento rozdíl je důležité, protože nespravované funkce často potřebují dereference, jak je znázorněno podpisy v prvním sloupci v následující tabulce. Spravovaná struktura a deklarace třídy ve zbývajících sloupců ukazují, do jaké míry, do kterého můžete upravit úroveň dereference ve vaší prohlášení. Deklarace jsou k dispozici pro Visual Basic a Visual C#.  
  
|Nespravovanému podpisu|Spravované deklarace: <br />žádné indirekce<br />`Structure MyType`<br />`struct MyType;`|Spravované deklarace: <br />jedna úroveň dereference<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Požadavky na nulu úrovněmi indirekce.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Přidá nulové úrovněmi indirekce.|Není možné, protože je již jedna úroveň dereference.|  
|`DoWork(MyType* x);`<br /><br /> Požadavky na jednu úroveň dereference.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Přidá jeden stupeň indirekce.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Přidá nulové úrovněmi indirekce.|  
|`DoWork(MyType** x);`<br /><br /> Požadavky na dvěma úrovněmi indirekce.|Není možné protože **ByRef** **ByRef** nebo `ref` `ref` nelze použít.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Přidá jeden stupeň indirekce.|  
  
 V tabulce jsou popsány následující pokyny pro deklarace volání nespravovaného kódu:  
  
-   Použijte strukturu, předán podle hodnoty, když toto nespravovaná funkce požaduje žádné dereference.  
  
-   Pomocí struktury předané referencí nebo třídu předán podle hodnoty, pokud nespravovaná funkce vyžaduje jednu úroveň dereference.  
  
-   Použití třídy předány podle odkazu, když je nespravované funkce požaduje dvěma úrovněmi indirekce.  
  
## <a name="declaring-and-passing-structures"></a>Deklarace a předávání struktur  
 Následující příklad ukazuje, jak definovat `Point` a `Rect` struktury v spravovaného kódu a předat jako parametr typů **PtInRect** funkce v souboru User32.dll. **PtInRect** má následující nespravovanému podpisu:  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Všimněte si, že musí předáte Rect – struktura odkazem, protože funkce očekává ukazatel na typ RECT.  
  
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
  
Friend Class WindowsAPI      
    Friend Shared Declare Auto Function PtInRect Lib "user32.dll" (
        ByRef r As Rect, p As Point) As Boolean  
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
  
internal static class WindowsAPI
{  
    [DllImport("User32.dll")]  
    internal static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a>Deklarace a předání třídy  
 Členy třídy můžete předat do nespravované funkci knihovny DLL jako třída má pevnou člen rozložení. Následující příklad ukazuje, jak předat členy `MySystemTime` třídy, které jsou definovány v postupném pořadí na **GetSystemTime** v souboru User32.dll. **GetSystemTime** má následující nespravovanému podpisu:  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Na rozdíl od hodnoty typů třídy mají vždy alespoň jednu úroveň dereference.  
  
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
  
Friend Class WindowsAPI  
    Friend Shared Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        sysTime As MySystemTime)  
    Friend Shared Declare Auto Function MessageBox Lib "User32.dll" (
        hWnd As IntPtr, lpText As String, lpCaption As String, uType As UInteger) As Integer  
End Class  
  
Public Class TestPlatformInvoke      
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        WindowsAPI.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        WindowsAPI.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)        
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
internal static class WindowsAPI
{  
    [DllImport("Kernel32.dll")]  
    internal static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet = CharSet.Auto)]  
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        WindowsAPI.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        WindowsAPI.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také:
- [Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
