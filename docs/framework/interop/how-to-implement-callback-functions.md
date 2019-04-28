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
ms.openlocfilehash: b0a033e6881f9c0c8741fda26211b0f565762de4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643085"
---
# <a name="how-to-implement-callback-functions"></a>Postupy: Implementace funkcí zpětného volání
Následující příklad a postupu ukazují, jak používat platformu vyvolání spravované aplikace, můžete vytisknout hodnotu popisovač pro každé okno v místním počítači. Konkrétně postup a ukázkovým použitím **EnumWindows** funkce krokovat seznamu windows a spravovaný zpětné volání – funkce (pojmenované zpětného volání) k tisku hodnoty popisovač okna.  
  
### <a name="to-implement-a-callback-function"></a>K implementaci funkce zpětného volání  
  
1. Podívejte se na podpis pro **EnumWindows** funkce než budete pokračovat s implementací. **EnumWindows** má následující podpis:  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     Jeden to naznačuje, že tato funkce vyžaduje zpětné volání spočívá v přítomnost **lpEnumFunc** argument. Je běžné zobrazíte **lp** předpony (dlouhým ukazatelem) v kombinaci s **Func** příponu názvu argumentů přijímajícími ukazatel na funkci zpětného volání. Dokumentaci k funkcím Win32 najdete v článku Microsoft Platform SDK.  
  
2. Vytvoření spravované zpětného volání funkce. Příklad deklaruje typ delegáta, volá `CallBack`, který přebírá dva argumenty (**hwnd** a **lparam**). První argument je popisovač okna. druhý argument je definované aplikací. V této verzi oba argumenty musí být celá čísla.  
  
     Funkce zpětného volání vrátí obecně nenulové hodnoty do značí úspěch a nula k označení selhání. V tomto příkladu explicitně nastaví návratovou hodnotu **true** pokračujte výčtu.  
  
3. Vytvoření delegáta a předat jako argument **EnumWindows** funkce. Vyvolání platformy automaticky převede formátu známé zpětné volání delegáta.  
  
4. Ujistěte se, že uvolňování nezíská delegáta předtím, než funkce zpětného volání dokončí svou práci. Při předání delegáta jako parametr nebo předání delegáta obsažená jako pole ve struktuře, zůstávají nesebraný po dobu trvání volání. Ano stejně jako v případě v následujícím příkladu výčet, funkce zpětného volání dokončí svou práci před volání vrátí a nevyžaduje žádné další akce spravované volající.  
  
     Pokud ale funkce zpětného volání lze vyvolat po volání se vrátí, spravované volající musí provést kroky k zajištění, že delegát zůstává nesebraný až do dokončení funkce zpětného volání. Podrobné informace o předcházení uvolňování paměti naleznete v tématu [zařazování Interop](../../../docs/framework/interop/interop-marshaling.md) pomocí vyvolání platformy.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Funkce zpětného volání](../../../docs/framework/interop/callback-functions.md)
- [Volání funkce DLL](../../../docs/framework/interop/calling-a-dll-function.md)
