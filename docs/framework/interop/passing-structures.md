---
title: Předávání struktur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
ms.openlocfilehash: 11e329fa8f0c059b6c2f1c8ccb1d6bd0d0f0030a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181341"
---
# <a name="passing-structures"></a>Předávání struktur
Mnoho nespravovaných funkcí očekává, že jako parametr funkce předáte členy struktur (uživatelem definované typy v jazyce Visual Basic) nebo členy tříd, které jsou definovány ve spravovaném kódu. Při předávání struktur nebo tříd nespravovaného kódu pomocí vyvolání platformy je nutné poskytnout další informace, aby se zachovalo původní rozložení a zarovnání. Toto téma <xref:System.Runtime.InteropServices.StructLayoutAttribute> představuje atribut, který slouží k definování formátovaných typů. Pro spravované struktury a třídy můžete vybrat z několika předvídatelné rozložení chování poskytované **výčtu LayoutKind.**  
  
 Ústředním bodem konceptů prezentovaných v tomto tématu je důležitý rozdíl mezi typy struktury a třídy. Struktury jsou typy hodnot a třídy jsou typy odkazů – třídy vždy poskytují alespoň jednu úroveň dereference paměti (ukazatel na hodnotu). Tento rozdíl je důležité, protože nespravované funkce často vyžadují dereference, jak je znázorněno podpisy v prvním sloupci následující tabulky. Spravovaná struktura a deklarace třídve zbývajících sloupcích zobrazují míru, do jaké můžete upravit úroveň dereference v deklaraci. Deklarace jsou k dispozici pro visual basic a visual c#.  
  
|Nespravovaný podpis|Spravovaná deklarace: <br />žádný dereference<br />`Structure MyType`<br />`struct MyType;`|Spravovaná deklarace: <br />jedna úroveň dereference<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Vyžaduje nulovou úroveň dereference.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Přidá nulové úrovně dereference.|Není to možné, protože již existuje jedna úroveň dereference.|  
|`DoWork(MyType* x);`<br /><br /> Vyžaduje jednu úroveň dereference.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Přidá jednu úroveň dereference.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Přidá nulové úrovně dereference.|  
|`DoWork(MyType** x);`<br /><br /> Vyžaduje dvě úrovně dereference.|Není možné, protože **ByRef** **ByRef** nebo `ref` `ref` nelze použít.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Přidá jednu úroveň dereference.|  
  
 Tabulka popisuje následující pokyny pro deklarace vyvolání platformy:  
  
- Použijte strukturu předanou hodnotou, když nespravovaná funkce nevyžaduje žádné dereference.  
  
- Použijte buď strukturu předanou odkazem, nebo třídu předanou hodnotou, když nespravovaná funkce vyžaduje jednu úroveň dereference.  
  
- Třídu předanou odkazem použijte, když nespravovaná funkce vyžaduje dvě úrovně dereference.  
  
## <a name="declaring-and-passing-structures"></a>Deklarování a předávání struktur  
 Následující příklad ukazuje, jak `Point` `Rect` definovat struktury a ve spravovaném kódu a předat typy jako parametr funkci **PtInRect** v souboru User32.dll. **PtInRect** má následující nespravovaný podpis:  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Všimněte si, že je nutné předat Rect struktury odkazem, protože funkce očekává ukazatel na typ RECT.  
  
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
  
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "user32.dll" (
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
  
internal static class NativeMethods
{  
    [DllImport("User32.dll")]  
    internal static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a>Deklarování a předávání tříd  
 Členy třídy můžete předat nespravované funkci DLL, pokud má třída pevné rozložení členů. Následující příklad ukazuje, jak předat `MySystemTime` členy třídy, které jsou definovány v sekvenčním pořadí, do **souboru GetSystemTime** v souboru User32.dll. **GetSystemTime** má následující nespravovaný podpis:  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Na rozdíl od typů hodnot mají třídy vždy alespoň jednu úroveň dereference.  
  
```vb  
Imports System.Runtime.InteropServices  
  
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
  
Friend Class NativeMethods  
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        sysTime As MySystemTime)  
    Friend Declare Auto Function MessageBox Lib "User32.dll" (
        hWnd As IntPtr, lpText As String, lpCaption As String, uType As UInteger) As Integer  
End Class  
  
Public Class TestPlatformInvoke
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        NativeMethods.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)
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
internal static class NativeMethods
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
        NativeMethods.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také

- [Volání funkce DLL](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
