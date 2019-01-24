---
title: 'Postupy: Implementace funkcí zpětného volání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- callback function, implementing
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bf972455aa54a7fe45ffd7858ac9e5da5eee6e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718673"
---
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="a3563-102">Postupy: Implementace funkcí zpětného volání</span><span class="sxs-lookup"><span data-stu-id="a3563-102">How to: Implement Callback Functions</span></span>
<span data-ttu-id="a3563-103">Následující příklad a postupu ukazují, jak používat platformu vyvolání spravované aplikace, můžete vytisknout hodnotu popisovač pro každé okno v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="a3563-103">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="a3563-104">Konkrétně postup a ukázkovým použitím **EnumWindows** funkce krokovat seznamu windows a spravovaný zpětné volání – funkce (pojmenované zpětného volání) k tisku hodnoty popisovač okna.</span><span class="sxs-lookup"><span data-stu-id="a3563-104">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="a3563-105">K implementaci funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="a3563-105">To implement a callback function</span></span>  
  
1.  <span data-ttu-id="a3563-106">Podívejte se na podpis pro **EnumWindows** funkce než budete pokračovat s implementací.</span><span class="sxs-lookup"><span data-stu-id="a3563-106">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="a3563-107">**EnumWindows** má následující podpis:</span><span class="sxs-lookup"><span data-stu-id="a3563-107">**EnumWindows** has the following signature:</span></span>  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     <span data-ttu-id="a3563-108">Jeden to naznačuje, že tato funkce vyžaduje zpětné volání spočívá v přítomnost **lpEnumFunc** argument.</span><span class="sxs-lookup"><span data-stu-id="a3563-108">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="a3563-109">Je běžné zobrazíte **lp** předpony (dlouhým ukazatelem) v kombinaci s **Func** příponu názvu argumentů přijímajícími ukazatel na funkci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="a3563-109">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="a3563-110">Dokumentaci k funkcím Win32 najdete v článku Microsoft Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="a3563-110">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2.  <span data-ttu-id="a3563-111">Vytvoření spravované zpětného volání funkce.</span><span class="sxs-lookup"><span data-stu-id="a3563-111">Create the managed callback function.</span></span> <span data-ttu-id="a3563-112">Příklad deklaruje typ delegáta, volá `CallBack`, který přebírá dva argumenty (**hwnd** a **lparam**).</span><span class="sxs-lookup"><span data-stu-id="a3563-112">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="a3563-113">První argument je popisovač okna. druhý argument je definované aplikací.</span><span class="sxs-lookup"><span data-stu-id="a3563-113">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="a3563-114">V této verzi oba argumenty musí být celá čísla.</span><span class="sxs-lookup"><span data-stu-id="a3563-114">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="a3563-115">Funkce zpětného volání vrátí obecně nenulové hodnoty do značí úspěch a nula k označení selhání.</span><span class="sxs-lookup"><span data-stu-id="a3563-115">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="a3563-116">V tomto příkladu explicitně nastaví návratovou hodnotu **true** pokračujte výčtu.</span><span class="sxs-lookup"><span data-stu-id="a3563-116">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3.  <span data-ttu-id="a3563-117">Vytvoření delegáta a předat jako argument **EnumWindows** funkce.</span><span class="sxs-lookup"><span data-stu-id="a3563-117">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="a3563-118">Vyvolání platformy automaticky převede formátu známé zpětné volání delegáta.</span><span class="sxs-lookup"><span data-stu-id="a3563-118">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4.  <span data-ttu-id="a3563-119">Ujistěte se, že uvolňování nezíská delegáta předtím, než funkce zpětného volání dokončí svou práci.</span><span class="sxs-lookup"><span data-stu-id="a3563-119">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="a3563-120">Při předání delegáta jako parametr nebo předání delegáta obsažená jako pole ve struktuře, zůstávají nesebraný po dobu trvání volání.</span><span class="sxs-lookup"><span data-stu-id="a3563-120">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="a3563-121">Ano stejně jako v případě v následujícím příkladu výčet, funkce zpětného volání dokončí svou práci před volání vrátí a nevyžaduje žádné další akce spravované volající.</span><span class="sxs-lookup"><span data-stu-id="a3563-121">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="a3563-122">Pokud ale funkce zpětného volání lze vyvolat po volání se vrátí, spravované volající musí provést kroky k zajištění, že delegát zůstává nesebraný až do dokončení funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="a3563-122">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="a3563-123">Podrobné informace o předcházení uvolňování paměti naleznete v tématu [zařazování Interop](../../../docs/framework/interop/interop-marshaling.md) pomocí vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="a3563-123">For detailed information about preventing garbage collection, see [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3563-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3563-124">Example</span></span>  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
  
Public Delegate Function CallBack( _  
hwnd As Integer, lParam As Integer) As Boolean  
  
Public Class EnumReportApp  
  
    Declare Function EnumWindows Lib "user32" ( _  
       x As CallBack, y As Integer) As Integer  
  
    Public Shared Sub Main()  
        EnumWindows(AddressOf EnumReportApp.Report, 0)  
    End Sub 'Main  
  
    Public Shared Function Report(hwnd As Integer, lParam As Integer) _  
    As Boolean  
        Console.Write("Window handle is ")  
        Console.WriteLine(hwnd)  
        Return True  
    End Function 'Report  
End Class 'EnumReportApp  
```  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public delegate bool CallBack(int hwnd, int lParam);  
  
public class EnumReportApp  
{  
    [DllImport("user32")]  
    public static extern int EnumWindows(CallBack x, int y);   
  
    public static void Main()   
    {  
        CallBack myCallBack = new CallBack(EnumReportApp.Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    public static bool Report(int hwnd, int lParam)  
    {   
        Console.Write("Window handle is ");  
        Console.WriteLine(hwnd);  
        return true;  
    }  
}  
```  
  
```cpp  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
// A delegate type.  
delegate bool CallBack(int hwnd, int lParam);  
  
// Managed type with the method to call.  
ref class EnumReport  
{  
// Report the window handle.  
public:  
    [DllImport("user32")]  
    static int EnumWindows(CallBack^ x, int y);  
  
    static void Main()  
    {  
        EnumReport^ er = gcnew EnumReport;  
        CallBack^ myCallBack = gcnew CallBack(&EnumReport::Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    static bool Report(int hwnd, int lParam)  
    {  
       Console::Write(L"Window handle is ");  
       Console::WriteLine(hwnd);  
       return true;  
    }  
};  
  
int main()  
{  
    EnumReport::Main();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3563-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3563-125">See also</span></span>
- [<span data-ttu-id="a3563-126">Funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="a3563-126">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)
- [<span data-ttu-id="a3563-127">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="a3563-127">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
