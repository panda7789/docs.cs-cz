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
# <a name="how-to-implement-callback-functions"></a>Postupy: Implementace funkcí zpětného volání
Následující postup a příklad ukazují, jak spravovaná aplikace, pomocí vyvolání platformy, může vytisknout hodnotu popisovače pro každé okno v místním počítači. Konkrétně postup a příklad používají funkci **EnumWindows** pro krokování seznamu oken a spravované funkce zpětného volání (pojmenované zpětné volání) k vytištění hodnoty popisovače okna.  
  
### <a name="to-implement-a-callback-function"></a>Implementace funkce zpětného volání  
  
1. Než budete pokračovat v implementaci, podívejte se na signaturu funkce **EnumWindows** . **EnumWindows** má následující signaturu:  
  
    ```cpp
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)
    ```
  
     Jedno potvrzení, že tato funkce vyžaduje zpětné volání, je přítomnost argumentu **lpEnumFunc** . Je běžné, že je v názvu argumentů, které přebírají ukazatel na funkci zpětného volání, v kombinaci s příponou **Func** zobrazená předpona **LP** (dlouhý ukazatel). Dokumentaci k funkcím Win32 naleznete v sadě Microsoft Platform SDK.  
  
2. Vytvořte spravovanou funkci zpětného volání. Příklad deklaruje typ delegáta, který se nazývá `CallBack`, který přijímá dva argumenty (**HWND** a **lParam**). První argument je popisovač okna. druhý argument je definován aplikací. V této verzi musí být oba argumenty celá čísla.  
  
     Funkce zpětného volání obecně vracejí nenulové hodnoty pro indikaci úspěšného a nulového označení selhání. Tento příklad explicitně nastaví návratovou hodnotu na **true** pro pokračování výčtu.  
  
3. Vytvořte delegáta a předejte ho jako argument funkci **EnumWindows** . Vyvolání platformy převede delegáta na známý formát zpětného volání automaticky.  
  
4. Zajistěte, aby systém uvolňování paměti nedeklaroval delegáta před tím, než funkce zpětného volání dokončí svou práci. Pokud předáte delegáta jako parametr nebo předáte delegáta, který je obsažen jako pole ve struktuře, zůstane po dobu trvání volání neshromažďováno. Podobně jako v následujícím příkladu výčtu funkce zpětného volání dokončí svou práci před vrácením volání a nevyžaduje od spravovaného volajícího žádné další akce.  
  
     Pokud se však funkce zpětného volání dá vyvolat po vrácení volání, spravované volající musí provést kroky, aby se zajistilo, že delegát zůstane neshromážděný, dokud funkce zpětného volání nedokončí. Podrobné informace o tom, jak zabránit uvolňování paměti, najdete v tématu věnovaném [vzájemnému zařazování](interop-marshaling.md) pomocí volání platforem.  
  
## <a name="example"></a>Příklad  
  
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
  
## <a name="see-also"></a>Viz také

- [Funkce zpětného volání](callback-functions.md)
- [Volání funkce DLL](calling-a-dll-function.md)
