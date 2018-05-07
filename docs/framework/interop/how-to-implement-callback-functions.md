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
---
# <a name="how-to-implement-callback-functions"></a>Postupy: Implementace funkcí zpětného volání
Následující postup a příklad ukazují, jak pomocí platformy vyvolání spravované aplikace, můžete vytisknout popisovač hodnota pro každé okno v místním počítači. Konkrétně postup a ukázkovým použitím **EnumWindows** funkci, aby se krok pomocí seznamu pro windows a spravovaný zpětného volání funkce (s názvem zpětného volání) k tisku hodnoty popisovač okna.  
  
### <a name="to-implement-a-callback-function"></a>K implementaci funkce zpětného volání  
  
1.  Podívejte se na podpis pro **EnumWindows** funkce než budete pokračovat s implementací. **EnumWindows** má následující podpis:  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     Jeden potvrzením, že tato funkce vyžaduje zpětné volání je přítomnost **lpEnumFunc** argument. Je běžné zobrazíte **lineárního programování úloh** předpony (dlouho ukazatel) v kombinaci s **Func** příponu názvu argumenty, které trvat ukazatel na funkci zpětného volání. Dokumentaci o Win32 funkcích najdete v tématu sady SDK pro platformu Microsoft.  
  
2.  Vytvoření funkce spravované zpětného volání. V příkladu deklaruje delegáta typu, s názvem `CallBack`, která má dva argumenty (**hwnd** a **lparam**). První argument je popisovač do okna; druhý argument je definované aplikací. V této verzi oba argumenty musí být celá čísla.  
  
     Funkce zpětného volání obecně vrátí nenulové hodnoty znamená úspěch a nula označující selhání. Tento příklad explicitně nastaví návratovou hodnotu na **true** pokračujte výčtu.  
  
3.  Vytvořte delegáta a předejte jej jako argument pro **EnumWindows** funkce. Vyvolání platformy automaticky převede delegát do formátu známé zpětného volání.  
  
4.  Ujistěte se, bude systém uvolňování před funkce zpětného volání nedokončí svoji práci nezíská delegát. Když předání delegáta jako parametr nebo předání delegáta obsažená jako pole ve struktuře, zůstane nesebraný po dobu trvání volání. Ano jak je tomu v následujícím příkladu výčtu, funkce zpětného volání nedokončí svoji práci předtím, než se volání vrátí a nevyžaduje žádné další akce spravované volající.  
  
     Pokud, ale funkce zpětného volání nelze vyvolat po volání vrátí, spravované volající musí provést kroky k zajištění, aby zůstala delegát nesebraný, dokud nebude dokončeno funkce zpětného volání. Podrobné informace o brání uvolňování paměti najdete v tématu [zařazování zprostředkovatel komunikace s objekty](../../../docs/framework/interop/interop-marshaling.md) s vyvolání platformy.  
  
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
 [Funkce zpětného volání](../../../docs/framework/interop/callback-functions.md)  
 [Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md)
