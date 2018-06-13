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
ms.openlocfilehash: e081347129ce367cf6b46ca29c07a016bb64ab95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389272"
---
# <a name="how-to-implement-callback-functions"></a><span data-ttu-id="40841-102">Postupy: Implementace funkcí zpětného volání</span><span class="sxs-lookup"><span data-stu-id="40841-102">How to: Implement Callback Functions</span></span>
<span data-ttu-id="40841-103">Následující postup a příklad ukazují, jak pomocí platformy vyvolání spravované aplikace, můžete vytisknout popisovač hodnota pro každé okno v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="40841-103">The following procedure and example demonstrate how a managed application, using platform invoke, can print the handle value for each window on the local computer.</span></span> <span data-ttu-id="40841-104">Konkrétně postup a ukázkovým použitím **EnumWindows** funkci, aby se krok pomocí seznamu pro windows a spravovaný zpětného volání funkce (s názvem zpětného volání) k tisku hodnoty popisovač okna.</span><span class="sxs-lookup"><span data-stu-id="40841-104">Specifically, the procedure and example use the **EnumWindows** function to step through the list of windows and a managed callback function (named CallBack) to print the value of the window handle.</span></span>  
  
### <a name="to-implement-a-callback-function"></a><span data-ttu-id="40841-105">K implementaci funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="40841-105">To implement a callback function</span></span>  
  
1.  <span data-ttu-id="40841-106">Podívejte se na podpis pro **EnumWindows** funkce než budete pokračovat s implementací.</span><span class="sxs-lookup"><span data-stu-id="40841-106">Look at the signature for the **EnumWindows** function before going further with the implementation.</span></span> <span data-ttu-id="40841-107">**EnumWindows** má následující podpis:</span><span class="sxs-lookup"><span data-stu-id="40841-107">**EnumWindows** has the following signature:</span></span>  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     <span data-ttu-id="40841-108">Jeden potvrzením, že tato funkce vyžaduje zpětné volání je přítomnost **lpEnumFunc** argument.</span><span class="sxs-lookup"><span data-stu-id="40841-108">One clue that this function requires a callback is the presence of the **lpEnumFunc** argument.</span></span> <span data-ttu-id="40841-109">Je běžné zobrazíte **lineárního programování úloh** předpony (dlouho ukazatel) v kombinaci s **Func** příponu názvu argumenty, které trvat ukazatel na funkci zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="40841-109">It is common to see the **lp** (long pointer) prefix combined with the **Func** suffix in the name of arguments that take a pointer to a callback function.</span></span> <span data-ttu-id="40841-110">Dokumentaci o Win32 funkcích najdete v tématu sady SDK pro platformu Microsoft.</span><span class="sxs-lookup"><span data-stu-id="40841-110">For documentation about Win32 functions, see the Microsoft Platform SDK.</span></span>  
  
2.  <span data-ttu-id="40841-111">Vytvoření funkce spravované zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="40841-111">Create the managed callback function.</span></span> <span data-ttu-id="40841-112">V příkladu deklaruje delegáta typu, s názvem `CallBack`, která má dva argumenty (**hwnd** a **lparam**).</span><span class="sxs-lookup"><span data-stu-id="40841-112">The example declares a delegate type, called `CallBack`, which takes two arguments (**hwnd** and **lparam**).</span></span> <span data-ttu-id="40841-113">První argument je popisovač do okna; druhý argument je definované aplikací.</span><span class="sxs-lookup"><span data-stu-id="40841-113">The first argument is a handle to the window; the second argument is application-defined.</span></span> <span data-ttu-id="40841-114">V této verzi oba argumenty musí být celá čísla.</span><span class="sxs-lookup"><span data-stu-id="40841-114">In this release, both arguments must be integers.</span></span>  
  
     <span data-ttu-id="40841-115">Funkce zpětného volání obecně vrátí nenulové hodnoty znamená úspěch a nula označující selhání.</span><span class="sxs-lookup"><span data-stu-id="40841-115">Callback functions generally return nonzero values to indicate success and zero to indicate failure.</span></span> <span data-ttu-id="40841-116">Tento příklad explicitně nastaví návratovou hodnotu na **true** pokračujte výčtu.</span><span class="sxs-lookup"><span data-stu-id="40841-116">This example explicitly sets the return value to **true** to continue the enumeration.</span></span>  
  
3.  <span data-ttu-id="40841-117">Vytvořte delegáta a předejte jej jako argument pro **EnumWindows** funkce.</span><span class="sxs-lookup"><span data-stu-id="40841-117">Create a delegate and pass it as an argument to the **EnumWindows** function.</span></span> <span data-ttu-id="40841-118">Vyvolání platformy automaticky převede delegát do formátu známé zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="40841-118">Platform invoke converts the delegate to a familiar callback format automatically.</span></span>  
  
4.  <span data-ttu-id="40841-119">Ujistěte se, bude systém uvolňování před funkce zpětného volání nedokončí svoji práci nezíská delegát.</span><span class="sxs-lookup"><span data-stu-id="40841-119">Ensure that the garbage collector does not reclaim the delegate before the callback function completes its work.</span></span> <span data-ttu-id="40841-120">Když předání delegáta jako parametr nebo předání delegáta obsažená jako pole ve struktuře, zůstane nesebraný po dobu trvání volání.</span><span class="sxs-lookup"><span data-stu-id="40841-120">When you pass a delegate as a parameter, or pass a delegate contained as a field in a structure, it remains uncollected for the duration of the call.</span></span> <span data-ttu-id="40841-121">Ano jak je tomu v následujícím příkladu výčtu, funkce zpětného volání nedokončí svoji práci předtím, než se volání vrátí a nevyžaduje žádné další akce spravované volající.</span><span class="sxs-lookup"><span data-stu-id="40841-121">So, as is the case in the following enumeration example, the callback function completes its work before the call returns and requires no additional action by the managed caller.</span></span>  
  
     <span data-ttu-id="40841-122">Pokud, ale funkce zpětného volání nelze vyvolat po volání vrátí, spravované volající musí provést kroky k zajištění, aby zůstala delegát nesebraný, dokud nebude dokončeno funkce zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="40841-122">If, however, the callback function can be invoked after the call returns, the managed caller must take steps to ensure that the delegate remains uncollected until the callback function finishes.</span></span> <span data-ttu-id="40841-123">Podrobné informace o brání uvolňování paměti najdete v tématu [zařazování zprostředkovatel komunikace s objekty](../../../docs/framework/interop/interop-marshaling.md) s vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="40841-123">For detailed information about preventing garbage collection, see [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md) with Platform Invoke.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40841-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="40841-124">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="40841-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="40841-125">See Also</span></span>  
 [<span data-ttu-id="40841-126">Funkce zpětného volání</span><span class="sxs-lookup"><span data-stu-id="40841-126">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)  
 [<span data-ttu-id="40841-127">Volání funkce DLL</span><span class="sxs-lookup"><span data-stu-id="40841-127">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
