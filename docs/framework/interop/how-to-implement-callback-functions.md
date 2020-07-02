---
title: 'Postupy: Implementace funkcí zpětného volání'
description: Podívejte se, jak implementovat funkce zpětného volání. V tomto příkladu spravovaná aplikace, která používá vyvolání platformy, vytiskne hodnotu popisovače pro každé okno v počítači.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- callback function, implementing
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
ms.openlocfilehash: 31c657372e760c8d57f9714b20178967ad85fcd3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619114"
---
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="bdd7b-104">Postupy: Implementace funkcí zpětného volání</span><span class="sxs-lookup"><span data-stu-id="bdd7b-104">How to: Implement Callback Functions</span></span>
<span data-ttu-id="bdd7b-105">Následující postup a příklad ukazují, jak spravovaná aplikace, pomocí vyvolání platformy, může vytisknout hodnotu popisovače pro každé okno v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-105">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="bdd7b-106">Konkrétně postup a příklad používají funkci **EnumWindows** pro krokování seznamu oken a spravované funkce zpětného volání (pojmenované zpětné volání) k vytištění hodnoty popisovače okna.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-106">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="bdd7b-107">Implementace funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="bdd7b-107">To implement a callback function</span></span>  
  
1. <span data-ttu-id="bdd7b-108">Než budete pokračovat v implementaci, podívejte se na signaturu funkce **EnumWindows** .</span><span class="sxs-lookup"><span data-stu-id="bdd7b-108">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="bdd7b-109">**EnumWindows** má následující signaturu:</span><span class="sxs-lookup"><span data-stu-id="bdd7b-109">**EnumWindows** has the following signature:</span></span>  
  
    ```cpp
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)
    ```
  
     <span data-ttu-id="bdd7b-110">Jedno potvrzení, že tato funkce vyžaduje zpětné volání, je přítomnost argumentu **lpEnumFunc** .</span><span class="sxs-lookup"><span data-stu-id="bdd7b-110">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="bdd7b-111">Je běžné, že je v názvu argumentů, které přebírají ukazatel na funkci zpětného volání, v kombinaci s příponou **Func** zobrazená předpona **LP** (dlouhý ukazatel).</span><span class="sxs-lookup"><span data-stu-id="bdd7b-111">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="bdd7b-112">Dokumentaci k funkcím Win32 naleznete v sadě Microsoft Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-112">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2. <span data-ttu-id="bdd7b-113">Vytvořte spravovanou funkci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-113">Create the managed callback function.</span></span> <span data-ttu-id="bdd7b-114">Příklad deklaruje typ delegáta, který se nazývá `CallBack` , který přijímá dva argumenty (**HWND** a **lParam**).</span><span class="sxs-lookup"><span data-stu-id="bdd7b-114">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="bdd7b-115">První argument je popisovač okna. druhý argument je definován aplikací.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-115">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="bdd7b-116">V této verzi musí být oba argumenty celá čísla.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-116">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="bdd7b-117">Funkce zpětného volání obecně vracejí nenulové hodnoty pro indikaci úspěšného a nulového označení selhání.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-117">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="bdd7b-118">Tento příklad explicitně nastaví návratovou hodnotu na **true** pro pokračování výčtu.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-118">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3. <span data-ttu-id="bdd7b-119">Vytvořte delegáta a předejte ho jako argument funkci **EnumWindows** .</span><span class="sxs-lookup"><span data-stu-id="bdd7b-119">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="bdd7b-120">Vyvolání platformy převede delegáta na známý formát zpětného volání automaticky.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-120">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4. <span data-ttu-id="bdd7b-121">Zajistěte, aby systém uvolňování paměti nedeklaroval delegáta před tím, než funkce zpětného volání dokončí svou práci.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-121">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="bdd7b-122">Pokud předáte delegáta jako parametr nebo předáte delegáta, který je obsažen jako pole ve struktuře, zůstane po dobu trvání volání neshromažďováno.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-122">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="bdd7b-123">Podobně jako v následujícím příkladu výčtu funkce zpětného volání dokončí svou práci před vrácením volání a nevyžaduje od spravovaného volajícího žádné další akce.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-123">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="bdd7b-124">Pokud se však funkce zpětného volání dá vyvolat po vrácení volání, spravované volající musí provést kroky, aby se zajistilo, že delegát zůstane neshromážděný, dokud funkce zpětného volání nedokončí.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-124">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="bdd7b-125">Podrobné informace o tom, jak zabránit uvolňování paměti, najdete v tématu věnovaném [vzájemnému zařazování](interop-marshaling.md) pomocí volání platforem.</span><span class="sxs-lookup"><span data-stu-id="bdd7b-125">For detailed information about preventing garbage collection, see [Interop Marshaling](interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdd7b-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="bdd7b-126">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bdd7b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdd7b-127">See also</span></span>

- [<span data-ttu-id="bdd7b-128">Funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="bdd7b-128">Callback Functions</span></span>](callback-functions.md)
- [<span data-ttu-id="bdd7b-129">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="bdd7b-129">Calling a DLL Function</span></span>](calling-a-dll-function.md)
