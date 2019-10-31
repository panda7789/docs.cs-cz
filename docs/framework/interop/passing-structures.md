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
# <a name="passing-structures"></a><span data-ttu-id="b8665-102">Předávání struktur</span><span class="sxs-lookup"><span data-stu-id="b8665-102">Passing Structures</span></span>
<span data-ttu-id="b8665-103">Mnoho nespravovaných funkcí očekává předání, jako parametr funkce, členů struktur (uživatelsky definovaných typů v Visual Basic) nebo členů tříd, které jsou definovány ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="b8665-103">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="b8665-104">Při předávání struktur nebo tříd do nespravovaného kódu pomocí vyvolání platformy je nutné zadat další informace, chcete-li zachovat původní rozložení a zarovnání.</span><span class="sxs-lookup"><span data-stu-id="b8665-104">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="b8665-105">Toto téma zavádí atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute>, který slouží k definování formátovaných typů.</span><span class="sxs-lookup"><span data-stu-id="b8665-105">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="b8665-106">Pro spravované struktury a třídy můžete vybrat z několika předvídatelných chování rozložení dodaných výčtem **LayoutKind** .</span><span class="sxs-lookup"><span data-stu-id="b8665-106">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="b8665-107">Střed k konceptům, které jsou uvedeny v tomto tématu, je důležitým rozdílem mezi strukturou a typy tříd.</span><span class="sxs-lookup"><span data-stu-id="b8665-107">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="b8665-108">Struktury jsou typy hodnot a třídy jsou odkazové typy – třídy vždy poskytují alespoň jednu úroveň indirekce paměti (ukazatel na hodnotu).</span><span class="sxs-lookup"><span data-stu-id="b8665-108">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="b8665-109">Tento rozdíl je důležitý, protože nespravované funkce často neodkazují na poptávku, jak je znázorněno v části signatury v prvním sloupci v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="b8665-109">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="b8665-110">Deklarace spravované struktury a třídy ve zbývajících sloupcích ukazuje míru, do které můžete upravit úroveň dereference v deklaraci. Deklarace jsou k dispozici pro Visual Basic i C#pro vizuál.</span><span class="sxs-lookup"><span data-stu-id="b8665-110">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="b8665-111">Nespravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="b8665-111">Unmanaged signature</span></span>|<span data-ttu-id="b8665-112">Spravovaná deklarace:</span><span class="sxs-lookup"><span data-stu-id="b8665-112">Managed declaration:</span></span> <br /><span data-ttu-id="b8665-113">bez indirekce</span><span class="sxs-lookup"><span data-stu-id="b8665-113">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="b8665-114">Spravovaná deklarace:</span><span class="sxs-lookup"><span data-stu-id="b8665-114">Managed declaration:</span></span> <br /><span data-ttu-id="b8665-115">Jedna úroveň dereference</span><span class="sxs-lookup"><span data-stu-id="b8665-115">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="b8665-116">Požaduje nulové úrovně dereference.</span><span class="sxs-lookup"><span data-stu-id="b8665-116">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="b8665-117">Přidává nulové úrovně dereference.</span><span class="sxs-lookup"><span data-stu-id="b8665-117">Adds zero levels of indirection.</span></span>|<span data-ttu-id="b8665-118">Nelze provést, protože již existuje jedna úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="b8665-118">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="b8665-119">Vyžaduje jednu úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="b8665-119">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="b8665-120">Přidá jednu úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="b8665-120">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="b8665-121">Přidává nulové úrovně dereference.</span><span class="sxs-lookup"><span data-stu-id="b8665-121">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="b8665-122">Požaduje dvě úrovně dereference.</span><span class="sxs-lookup"><span data-stu-id="b8665-122">Demands two levels of indirection.</span></span>|<span data-ttu-id="b8665-123">Možnost **ByRef** **byref** nebo `ref` `ref` nelze použít.</span><span class="sxs-lookup"><span data-stu-id="b8665-123">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="b8665-124">Přidá jednu úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="b8665-124">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="b8665-125">Tabulka popisuje následující pokyny pro deklarace volání platforem:</span><span class="sxs-lookup"><span data-stu-id="b8665-125">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
- <span data-ttu-id="b8665-126">Použijte strukturu předanou hodnotou, pokud nespravovaná funkce nepožaduje žádné indirekce.</span><span class="sxs-lookup"><span data-stu-id="b8665-126">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
- <span data-ttu-id="b8665-127">Použijte buď strukturu předanou odkazem, nebo třídu předanou hodnotou, pokud nespravovaná funkce vyžaduje jednu úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="b8665-127">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
- <span data-ttu-id="b8665-128">Použijte třídu předanou odkazem, pokud nespravovaná funkce požaduje dvě úrovně dereference.</span><span class="sxs-lookup"><span data-stu-id="b8665-128">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="b8665-129">Deklarace a předávání struktur</span><span class="sxs-lookup"><span data-stu-id="b8665-129">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="b8665-130">Následující příklad ukazuje, jak definovat `Point` a `Rect` struktury ve spravovaném kódu a předat typy jako parametr funkci **PtInRect** v souboru User32. dll.</span><span class="sxs-lookup"><span data-stu-id="b8665-130">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="b8665-131">**PtInRect** má následující nespravovaný podpis:</span><span class="sxs-lookup"><span data-stu-id="b8665-131">**PtInRect** has the following unmanaged signature:</span></span>  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="b8665-132">Všimněte si, že je nutné předat strukturu Rect odkazem, protože funkce očekává ukazatel na typ RECT.</span><span class="sxs-lookup"><span data-stu-id="b8665-132">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
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
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="b8665-133">Deklarace a předávání tříd</span><span class="sxs-lookup"><span data-stu-id="b8665-133">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="b8665-134">Můžete předat členy třídy do nespravované funkce knihovny DLL, pokud má třída pevné členské rozložení.</span><span class="sxs-lookup"><span data-stu-id="b8665-134">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="b8665-135">Následující příklad ukazuje, jak předat členy třídy `MySystemTime`, které jsou definovány v sekvenčním pořadí, do **GetSystemTime** v souboru User32. dll.</span><span class="sxs-lookup"><span data-stu-id="b8665-135">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="b8665-136">**GetSystemTime** má následující nespravovaný podpis:</span><span class="sxs-lookup"><span data-stu-id="b8665-136">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="b8665-137">Na rozdíl od hodnotových typů mají třídy vždy alespoň jednu úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="b8665-137">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b8665-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8665-138">See also</span></span>

- [<span data-ttu-id="b8665-139">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="b8665-139">Calling a DLL Function</span></span>](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
