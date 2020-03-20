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
ms.openlocfilehash: b7aae1e70ac736d60bed1e79291235db1c220281
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181419"
---
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="2c6ca-102">Postupy: Implementace funkcí zpětného volání</span><span class="sxs-lookup"><span data-stu-id="2c6ca-102">How to: Implement Callback Functions</span></span>
<span data-ttu-id="2c6ca-103">Následující postup a příklad ukazují, jak spravovaná aplikace pomocí platformy invoke může vytisknout hodnotu popisovače pro každé okno v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-103">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="2c6ca-104">Konkrétně postup a příklad použít **EnumWindows** funkce krokovat seznam oken a spravované funkce zpětného volání (s názvem Zpětné volání) vytisknout hodnotu popisovače okna.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-104">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="2c6ca-105">Implementace funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="2c6ca-105">To implement a callback function</span></span>  
  
1. <span data-ttu-id="2c6ca-106">Podívejte se na podpis pro funkci **EnumWindows** před přejde dále s implementací.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-106">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="2c6ca-107">**EnumWindows** má následující podpis:</span><span class="sxs-lookup"><span data-stu-id="2c6ca-107">**EnumWindows** has the following signature:</span></span>  
  
    ```cpp
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)
    ```
  
     <span data-ttu-id="2c6ca-108">Jedna stopa, že tato funkce vyžaduje zpětné volání je přítomnost **lpEnumFunc** argument.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-108">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="2c6ca-109">Je běžné vidět **lp** (dlouhý ukazatel) předponu v kombinaci s příponou **Func** v názvu argumentů, které převzít ukazatel na funkci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-109">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="2c6ca-110">Dokumentaci k funkcím win32 naleznete v sadě Microsoft Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-110">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2. <span data-ttu-id="2c6ca-111">Vytvořte funkci spravovaného zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-111">Create the managed callback function.</span></span> <span data-ttu-id="2c6ca-112">Příklad deklaruje typ `CallBack`delegáta s názvem , který přebírá dva argumenty (**hwnd** a **lparam**).</span><span class="sxs-lookup"><span data-stu-id="2c6ca-112">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="2c6ca-113">První argument je popisovač okna; druhý argument je definován aplikací.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-113">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="2c6ca-114">V této verzi musí být oba argumenty celá čísla.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-114">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="2c6ca-115">Funkce zpětného volání obecně vrátit nenulové hodnoty označující úspěch a nula označuje selhání.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-115">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="2c6ca-116">Tento příklad explicitně nastaví vrácenou hodnotu na **hodnotu true,** aby bylo pokračovat ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-116">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3. <span data-ttu-id="2c6ca-117">Vytvořte delegáta a předajte jej jako argument funkci **EnumWindows.**</span><span class="sxs-lookup"><span data-stu-id="2c6ca-117">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="2c6ca-118">Vyvolání platformy automaticky převede delegáta na známý formát zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-118">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4. <span data-ttu-id="2c6ca-119">Ujistěte se, že systém uvolňování paměti nezíská delegáta před dokončením práce funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-119">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="2c6ca-120">Když předáte delegáta jako parametr nebo předat delegáta obsaženého jako pole ve struktuře, zůstane nevybrané po dobu trvání volání.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-120">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="2c6ca-121">Tak, jak je tomu v následujícím příkladu výčtu, funkce zpětného volání dokončí svou práci před volání vrátí a nevyžaduje žádnou další akci spravovaného volajícího.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-121">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="2c6ca-122">Pokud však funkce zpětného volání může být vyvolána po návratu volání, spravovaný volající musí podniknout kroky k zajištění, že delegát zůstane nesebrané, dokud nebude dokončena funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-122">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="2c6ca-123">Podrobné informace o zabránění uvolňování paměti naleznete [v tématu Interop zařazování](interop-marshaling.md) s platformy invoke.</span><span class="sxs-lookup"><span data-stu-id="2c6ca-123">For detailed information about preventing garbage collection, see [Interop Marshaling](interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c6ca-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c6ca-124">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c6ca-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c6ca-125">See also</span></span>

- [<span data-ttu-id="2c6ca-126">Funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="2c6ca-126">Callback Functions</span></span>](callback-functions.md)
- [<span data-ttu-id="2c6ca-127">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="2c6ca-127">Calling a DLL Function</span></span>](calling-a-dll-function.md)
