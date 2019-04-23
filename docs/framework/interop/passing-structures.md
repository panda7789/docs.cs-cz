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
ms.openlocfilehash: c8e35a09bd3348d5f53c662cf6e0ee9fec733d88
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142815"
---
# <a name="passing-structures"></a><span data-ttu-id="c98e5-102">Předávání struktur</span><span class="sxs-lookup"><span data-stu-id="c98e5-102">Passing Structures</span></span>
<span data-ttu-id="c98e5-103">Mnoho nespravovaných funkcí očekávat předat jako parametr pro funkci, členové struktur (uživatelem definované typy v jazyce Visual Basic) nebo členy třídy, které jsou definovány ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="c98e5-103">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="c98e5-104">Při předávání struktur nebo tříd do nespravovaného kódu pomocí platformy vyvolat, je třeba zadat další informace a zachovat původní rozložení a zarovnání.</span><span class="sxs-lookup"><span data-stu-id="c98e5-104">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="c98e5-105">Toto téma představuje <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut, který slouží k definování formátovaný typy.</span><span class="sxs-lookup"><span data-stu-id="c98e5-105">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="c98e5-106">Pro spravované struktur a tříd, můžete vybrat z několika chování předvídatelné rozložení poskytnutých **LayoutKind** výčtu.</span><span class="sxs-lookup"><span data-stu-id="c98e5-106">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="c98e5-107">Z centrální na koncepty v tomto tématu je důležitý rozdíl mezi typy struktury a třídy.</span><span class="sxs-lookup"><span data-stu-id="c98e5-107">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="c98e5-108">Struktury jsou typy hodnot a třídy jsou odkazové typy – třídy poskytují vždy alespoň jednu úroveň dereference paměti (ukazatel na hodnotu).</span><span class="sxs-lookup"><span data-stu-id="c98e5-108">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="c98e5-109">Tento rozdíl je důležité, protože nespravované funkce často potřebují dereference, jak je znázorněno podpisy v prvním sloupci v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="c98e5-109">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="c98e5-110">Spravovaná struktura a deklarace třídy ve zbývajících sloupců ukazují, do jaké míry, do kterého můžete upravit úroveň dereference ve vaší prohlášení. Deklarace jsou k dispozici pro Visual Basic a Visual C#.</span><span class="sxs-lookup"><span data-stu-id="c98e5-110">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="c98e5-111">Nespravovanému podpisu</span><span class="sxs-lookup"><span data-stu-id="c98e5-111">Unmanaged signature</span></span>|<span data-ttu-id="c98e5-112">Spravované deklarace:</span><span class="sxs-lookup"><span data-stu-id="c98e5-112">Managed declaration:</span></span> <br /><span data-ttu-id="c98e5-113">žádné indirekce</span><span class="sxs-lookup"><span data-stu-id="c98e5-113">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="c98e5-114">Spravované deklarace:</span><span class="sxs-lookup"><span data-stu-id="c98e5-114">Managed declaration:</span></span> <br /><span data-ttu-id="c98e5-115">jedna úroveň dereference</span><span class="sxs-lookup"><span data-stu-id="c98e5-115">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="c98e5-116">Požadavky na nulu úrovněmi indirekce.</span><span class="sxs-lookup"><span data-stu-id="c98e5-116">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="c98e5-117">Přidá nulové úrovněmi indirekce.</span><span class="sxs-lookup"><span data-stu-id="c98e5-117">Adds zero levels of indirection.</span></span>|<span data-ttu-id="c98e5-118">Není možné, protože je již jedna úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="c98e5-118">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="c98e5-119">Požadavky na jednu úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="c98e5-119">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="c98e5-120">Přidá jeden stupeň indirekce.</span><span class="sxs-lookup"><span data-stu-id="c98e5-120">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="c98e5-121">Přidá nulové úrovněmi indirekce.</span><span class="sxs-lookup"><span data-stu-id="c98e5-121">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="c98e5-122">Požadavky na dvěma úrovněmi indirekce.</span><span class="sxs-lookup"><span data-stu-id="c98e5-122">Demands two levels of indirection.</span></span>|<span data-ttu-id="c98e5-123">Není možné protože **ByRef** **ByRef** nebo `ref` `ref` nelze použít.</span><span class="sxs-lookup"><span data-stu-id="c98e5-123">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="c98e5-124">Přidá jeden stupeň indirekce.</span><span class="sxs-lookup"><span data-stu-id="c98e5-124">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="c98e5-125">V tabulce jsou popsány následující pokyny pro deklarace volání nespravovaného kódu:</span><span class="sxs-lookup"><span data-stu-id="c98e5-125">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
-   <span data-ttu-id="c98e5-126">Použijte strukturu, předán podle hodnoty, když toto nespravovaná funkce požaduje žádné dereference.</span><span class="sxs-lookup"><span data-stu-id="c98e5-126">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
-   <span data-ttu-id="c98e5-127">Pomocí struktury předané referencí nebo třídu předán podle hodnoty, pokud nespravovaná funkce vyžaduje jednu úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="c98e5-127">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
-   <span data-ttu-id="c98e5-128">Použití třídy předány podle odkazu, když je nespravované funkce požaduje dvěma úrovněmi indirekce.</span><span class="sxs-lookup"><span data-stu-id="c98e5-128">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="c98e5-129">Deklarace a předávání struktur</span><span class="sxs-lookup"><span data-stu-id="c98e5-129">Declaring and Passing Structures</span></span>  
 <span data-ttu-id="c98e5-130">Následující příklad ukazuje, jak definovat `Point` a `Rect` struktury v spravovaného kódu a předat jako parametr typů **PtInRect** funkce v souboru User32.dll.</span><span class="sxs-lookup"><span data-stu-id="c98e5-130">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="c98e5-131">**PtInRect** má následující nespravovanému podpisu:</span><span class="sxs-lookup"><span data-stu-id="c98e5-131">**PtInRect** has the following unmanaged signature:</span></span>  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="c98e5-132">Všimněte si, že musí předáte Rect – struktura odkazem, protože funkce očekává ukazatel na typ RECT.</span><span class="sxs-lookup"><span data-stu-id="c98e5-132">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
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
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="c98e5-133">Deklarace a předání třídy</span><span class="sxs-lookup"><span data-stu-id="c98e5-133">Declaring and Passing Classes</span></span>  
 <span data-ttu-id="c98e5-134">Členy třídy můžete předat do nespravované funkci knihovny DLL jako třída má pevnou člen rozložení.</span><span class="sxs-lookup"><span data-stu-id="c98e5-134">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="c98e5-135">Následující příklad ukazuje, jak předat členy `MySystemTime` třídy, které jsou definovány v postupném pořadí na **GetSystemTime** v souboru User32.dll.</span><span class="sxs-lookup"><span data-stu-id="c98e5-135">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="c98e5-136">**GetSystemTime** má následující nespravovanému podpisu:</span><span class="sxs-lookup"><span data-stu-id="c98e5-136">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="c98e5-137">Na rozdíl od hodnoty typů třídy mají vždy alespoň jednu úroveň dereference.</span><span class="sxs-lookup"><span data-stu-id="c98e5-137">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c98e5-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c98e5-138">See also</span></span>

- [<span data-ttu-id="c98e5-139">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="c98e5-139">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
