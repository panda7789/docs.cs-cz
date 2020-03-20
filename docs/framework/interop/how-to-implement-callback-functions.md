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
Následující postup a příklad ukazují, jak spravovaná aplikace pomocí platformy invoke může vytisknout hodnotu popisovače pro každé okno v místním počítači. Konkrétně postup a příklad použít **EnumWindows** funkce krokovat seznam oken a spravované funkce zpětného volání (s názvem Zpětné volání) vytisknout hodnotu popisovače okna.  
  
### <a name="to-implement-a-callback-function"></a>Implementace funkce zpětného volání  
  
1. Podívejte se na podpis pro funkci **EnumWindows** před přejde dále s implementací. **EnumWindows** má následující podpis:  
  
    ```cpp
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)
    ```
  
     Jedna stopa, že tato funkce vyžaduje zpětné volání je přítomnost **lpEnumFunc** argument. Je běžné vidět **lp** (dlouhý ukazatel) předponu v kombinaci s příponou **Func** v názvu argumentů, které převzít ukazatel na funkci zpětného volání. Dokumentaci k funkcím win32 naleznete v sadě Microsoft Platform SDK.  
  
2. Vytvořte funkci spravovaného zpětného volání. Příklad deklaruje typ `CallBack`delegáta s názvem , který přebírá dva argumenty (**hwnd** a **lparam**). První argument je popisovač okna; druhý argument je definován aplikací. V této verzi musí být oba argumenty celá čísla.  
  
     Funkce zpětného volání obecně vrátit nenulové hodnoty označující úspěch a nula označuje selhání. Tento příklad explicitně nastaví vrácenou hodnotu na **hodnotu true,** aby bylo pokračovat ve výčtu.  
  
3. Vytvořte delegáta a předajte jej jako argument funkci **EnumWindows.** Vyvolání platformy automaticky převede delegáta na známý formát zpětného volání.  
  
4. Ujistěte se, že systém uvolňování paměti nezíská delegáta před dokončením práce funkce zpětného volání. Když předáte delegáta jako parametr nebo předat delegáta obsaženého jako pole ve struktuře, zůstane nevybrané po dobu trvání volání. Tak, jak je tomu v následujícím příkladu výčtu, funkce zpětného volání dokončí svou práci před volání vrátí a nevyžaduje žádnou další akci spravovaného volajícího.  
  
     Pokud však funkce zpětného volání může být vyvolána po návratu volání, spravovaný volající musí podniknout kroky k zajištění, že delegát zůstane nesebrané, dokud nebude dokončena funkce zpětného volání. Podrobné informace o zabránění uvolňování paměti naleznete [v tématu Interop zařazování](interop-marshaling.md) s platformy invoke.  
  
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
