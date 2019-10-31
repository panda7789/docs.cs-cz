---
title: Předávání struktur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
ms.openlocfilehash: 8fde48f0697d986c5fc7f6d7059b6b45a6af1488
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124983"
---
# <a name="passing-structures"></a>Předávání struktur
Mnoho nespravovaných funkcí očekává předání, jako parametr funkce, členů struktur (uživatelsky definovaných typů v Visual Basic) nebo členů tříd, které jsou definovány ve spravovaném kódu. Při předávání struktur nebo tříd do nespravovaného kódu pomocí vyvolání platformy je nutné zadat další informace, chcete-li zachovat původní rozložení a zarovnání. Toto téma zavádí atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute>, který slouží k definování formátovaných typů. Pro spravované struktury a třídy můžete vybrat z několika předvídatelných chování rozložení dodaných výčtem **LayoutKind** .  
  
 Střed k konceptům, které jsou uvedeny v tomto tématu, je důležitým rozdílem mezi strukturou a typy tříd. Struktury jsou typy hodnot a třídy jsou odkazové typy – třídy vždy poskytují alespoň jednu úroveň indirekce paměti (ukazatel na hodnotu). Tento rozdíl je důležitý, protože nespravované funkce často neodkazují na poptávku, jak je znázorněno v části signatury v prvním sloupci v následující tabulce. Deklarace spravované struktury a třídy ve zbývajících sloupcích ukazuje míru, do které můžete upravit úroveň dereference v deklaraci. Deklarace jsou k dispozici pro Visual Basic i C#pro vizuál.  
  
|Nespravovaný podpis|Spravovaná deklarace: <br />bez indirekce<br />`Structure MyType`<br />`struct MyType;`|Spravovaná deklarace: <br />Jedna úroveň dereference<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Požaduje nulové úrovně dereference.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Přidává nulové úrovně dereference.|Nelze provést, protože již existuje jedna úroveň dereference.|  
|`DoWork(MyType* x);`<br /><br /> Vyžaduje jednu úroveň dereference.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Přidá jednu úroveň dereference.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Přidává nulové úrovně dereference.|  
|`DoWork(MyType** x);`<br /><br /> Požaduje dvě úrovně dereference.|Možnost **ByRef** **byref** nebo `ref` `ref` nelze použít.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Přidá jednu úroveň dereference.|  
  
 Tabulka popisuje následující pokyny pro deklarace volání platforem:  
  
- Použijte strukturu předanou hodnotou, pokud nespravovaná funkce nepožaduje žádné indirekce.  
  
- Použijte buď strukturu předanou odkazem, nebo třídu předanou hodnotou, pokud nespravovaná funkce vyžaduje jednu úroveň dereference.  
  
- Použijte třídu předanou odkazem, pokud nespravovaná funkce požaduje dvě úrovně dereference.  
  
## <a name="declaring-and-passing-structures"></a>Deklarace a předávání struktur  
 Následující příklad ukazuje, jak definovat `Point` a `Rect` struktury ve spravovaném kódu a předat typy jako parametr funkci **PtInRect** v souboru User32. dll. **PtInRect** má následující nespravovaný podpis:  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Všimněte si, že je nutné předat strukturu Rect odkazem, protože funkce očekává ukazatel na typ RECT.  
  
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
  
## <a name="declaring-and-passing-classes"></a>Deklarace a předávání tříd  
 Můžete předat členy třídy do nespravované funkce knihovny DLL, pokud má třída pevné členské rozložení. Následující příklad ukazuje, jak předat členy třídy `MySystemTime`, které jsou definovány v sekvenčním pořadí, do **GetSystemTime** v souboru User32. dll. **GetSystemTime** má následující nespravovaný podpis:  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Na rozdíl od hodnotových typů mají třídy vždy alespoň jednu úroveň dereference.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Volání funkce DLL](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
