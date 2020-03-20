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
# <a name="passing-structures"></a><span data-ttu-id="54e4e-102">Předávání struktur</span><span class="sxs-lookup"><span data-stu-id="54e4e-102">Passing Structures</span></span>
<span data-ttu-id="54e4e-103">Mnoho nespravovaných funkcí očekává, že jako parametr funkce předáte členy struktur (uživatelem definované typy v jazyce Visual Basic) nebo členy tříd, které jsou definovány ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="54e4e-103">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="54e4e-104">Při předávání struktur nebo tříd nespravovaného kódu pomocí vyvolání platformy je nutné poskytnout další informace, aby se zachovalo původní rozložení a zarovnání.</span><span class="sxs-lookup"><span data-stu-id="54e4e-104">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="54e4e-105">Toto téma <xref:System.Runtime.InteropServices.StructLayoutAttribute> představuje atribut, který slouží k definování formátovaných typů.</span><span class="sxs-lookup"><span data-stu-id="54e4e-105">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="54e4e-106">Pro spravované struktury a třídy můžete vybrat z několika předvídatelné rozložení chování poskytované **výčtu LayoutKind.**</span><span class="sxs-lookup"><span data-stu-id="54e4e-106">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="54e4e-107">Ústředním bodem konceptů prezentovaných v tomto tématu je důležitý rozdíl mezi typy struktury a třídy.</span><span class="sxs-lookup"><span data-stu-id="54e4e-107">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="54e4e-108">Struktury jsou typy hodnot a třídy jsou typy odkazů – třídy vždy poskytují alespoň jednu úroveň dereference paměti (ukazatel na hodnotu).</span><span class="sxs-lookup"><span data-stu-id="54e4e-108">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="54e4e-109">Tento rozdíl je důležité, protože nespravované funkce často vyžadují dereference, jak je znázorněno podpisy v prvním sloupci následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="54e4e-109">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="54e4e-110">Spravovaná struktura a deklarace třídve zbývajících sloupcích zobrazují míru, do jaké můžete upravit úroveň dereference v deklaraci. Deklarace jsou k dispozici pro visual basic a visual c#.</span><span class="sxs-lookup"><span data-stu-id="54e4e-110">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="54e4e-111">Nespravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="54e4e-111">Unmanaged signature</span></span>|<span data-ttu-id="54e4e-112">Spravovaná deklarace:</span><span class="sxs-lookup"><span data-stu-id="54e4e-112">Managed declaration:</span></span> <br /><span data-ttu-id="54e4e-113">žádný dereference</span><span class="sxs-lookup"><span data-stu-id="54e4e-113">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="54e4e-114">Spravovaná deklarace:</span><span class="sxs-lookup"><span data-stu-id="54e4e-114">Managed declaration:</span></span> <br /><span data-ttu-id="54e4e-115">jedna úroveň dereference</span><span class="sxs-lookup"><span data-stu-id="54e4e-115">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="54e4e-116">Vyžaduje nulovou úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="54e4e-116">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="54e4e-117">Přidá nulové úrovně dereference.</span><span class="sxs-lookup"><span data-stu-id="54e4e-117">Adds zero levels of indirection.</span></span>|<span data-ttu-id="54e4e-118">Není to možné, protože již existuje jedna úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="54e4e-118">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="54e4e-119">Vyžaduje jednu úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="54e4e-119">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="54e4e-120">Přidá jednu úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="54e4e-120">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="54e4e-121">Přidá nulové úrovně dereference.</span><span class="sxs-lookup"><span data-stu-id="54e4e-121">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="54e4e-122">Vyžaduje dvě úrovně dereference.</span><span class="sxs-lookup"><span data-stu-id="54e4e-122">Demands two levels of indirection.</span></span>|<span data-ttu-id="54e4e-123">Není možné, protože **ByRef** **ByRef** nebo `ref` `ref` nelze použít.</span><span class="sxs-lookup"><span data-stu-id="54e4e-123">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="54e4e-124">Přidá jednu úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="54e4e-124">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="54e4e-125">Tabulka popisuje následující pokyny pro deklarace vyvolání platformy:</span><span class="sxs-lookup"><span data-stu-id="54e4e-125">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
- <span data-ttu-id="54e4e-126">Použijte strukturu předanou hodnotou, když nespravovaná funkce nevyžaduje žádné dereference.</span><span class="sxs-lookup"><span data-stu-id="54e4e-126">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
- <span data-ttu-id="54e4e-127">Použijte buď strukturu předanou odkazem, nebo třídu předanou hodnotou, když nespravovaná funkce vyžaduje jednu úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="54e4e-127">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
- <span data-ttu-id="54e4e-128">Třídu předanou odkazem použijte, když nespravovaná funkce vyžaduje dvě úrovně dereference.</span><span class="sxs-lookup"><span data-stu-id="54e4e-128">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="54e4e-129">Deklarování a předávání struktur</span><span class="sxs-lookup"><span data-stu-id="54e4e-129">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="54e4e-130">Následující příklad ukazuje, jak `Point` `Rect` definovat struktury a ve spravovaném kódu a předat typy jako parametr funkci **PtInRect** v souboru User32.dll.</span><span class="sxs-lookup"><span data-stu-id="54e4e-130">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="54e4e-131">**PtInRect** má následující nespravovaný podpis:</span><span class="sxs-lookup"><span data-stu-id="54e4e-131">**PtInRect** has the following unmanaged signature:</span></span>  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="54e4e-132">Všimněte si, že je nutné předat Rect struktury odkazem, protože funkce očekává ukazatel na typ RECT.</span><span class="sxs-lookup"><span data-stu-id="54e4e-132">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
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
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="54e4e-133">Deklarování a předávání tříd</span><span class="sxs-lookup"><span data-stu-id="54e4e-133">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="54e4e-134">Členy třídy můžete předat nespravované funkci DLL, pokud má třída pevné rozložení členů.</span><span class="sxs-lookup"><span data-stu-id="54e4e-134">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="54e4e-135">Následující příklad ukazuje, jak předat `MySystemTime` členy třídy, které jsou definovány v sekvenčním pořadí, do **souboru GetSystemTime** v souboru User32.dll.</span><span class="sxs-lookup"><span data-stu-id="54e4e-135">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="54e4e-136">**GetSystemTime** má následující nespravovaný podpis:</span><span class="sxs-lookup"><span data-stu-id="54e4e-136">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="54e4e-137">Na rozdíl od typů hodnot mají třídy vždy alespoň jednu úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="54e4e-137">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54e4e-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="54e4e-138">See also</span></span>

- [<span data-ttu-id="54e4e-139">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="54e4e-139">Calling a DLL Function</span></span>](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
