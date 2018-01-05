---
title: "Výchozí zařazování pro řetězce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f8de04f9674e67bf1498fb8f25f2b3c61fec438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="default-marshaling-for-strings"></a>Výchozí zařazování pro řetězce
Jak <xref:System.String?displayProperty=nameWithType> a <xref:System.Text.StringBuilder?displayProperty=nameWithType> třídy mají podobné chování zařazování.  
  
 Řetězce jsou zařazené jako stylu COM `BSTR` typu nebo jako řetězce ukončené hodnotou null (pole znaků, který končí znak hodnoty null). Můžete zařadit znaky v řetězci, jako kódování Unicode (výchozí nastavení v systémech Windows) nebo ANSI.  
  
 Toto téma obsahuje následující informace na zařazování typů řetězec:  
  
-   [Řetězce používané v rozhraních](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [Vyvolání řetězce použité v platformě](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [Řetězce použité v struktury](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [Řetězce pevné délky vyrovnávací paměti](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>   
## <a name="strings-used-in-interfaces"></a>Řetězce používané v rozhraních  
 V následující tabulce jsou uvedeny možnosti zařazování pro datový typ řetězec při zařazené jako argument metody na nespravovaný kód. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnoty výčtu k zařazování řetězců do rozhraní COM.  
  
|Typ výčtu|Popis nespravované formátu|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`(výchozí)|COM – styl `BSTR` s předponou délku a znaky znakové sady Unicode.|  
|`UnmanagedType.LPStr`|Ukazatel pole znaků ANSI ukončené hodnotou null.|  
|`UnmanagedType.LPWStr`|Ukazatel na pole znaků Unicode ukončené hodnotou null.|  
  
 Tato tabulka platí pro řetězce. Ale pro <xref:System.Text.StringBuilder>, jsou povoleny pouze možnosti `UnmanagedType.LPStr` a `UnmanagedType.LPWStr`.  
  
 Následující příklad ukazuje řetězce v deklarována `IStringWorker` rozhraní.  
  
```cpp  
public interface IStringWorker {  
void PassString1(String s);  
void PassString2([MarshalAs(UnmanagedType.BStr)]String s);  
void PassString3([MarshalAs(UnmanagedType.LPStr)]String s);  
void PassString4([MarshalAs(UnmanagedType.LPWStr)]String s);  
void PassStringRef1(ref String s);  
void PassStringRef2([MarshalAs(UnmanagedType.BStr)]ref String s);  
void PassStringRef3([MarshalAs(UnmanagedType.LPStr)]ref String s);  
void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)]ref String s);  
);  
```  
  
 Následující příklad ukazuje odpovídající rozhraní, které jsou popsané v knihovny typů.  
  
```  
[…]  
interface IStringWorker : IDispatch {  
HRESULT PassString1([in] BSTR s);  
HRESULT PassString2([in] BSTR s);  
HRESULT PassString3([in] LPStr s);  
HRESULT PassString4([in] LPWStr s);  
HRESULT PassStringRef1([in, out] BSTR *s);  
HRESULT PassStringRef2([in, out] BSTR *s);  
HRESULT PassStringRef3([in, out] LPStr *s);  
HRESULT PassStringRef4([in, out] LPWStr *s);  
);  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor5"></a>   
## <a name="strings-used-in-platform-invoke"></a>Vyvolání řetězce použité v platformě  
 Vyvolání platformy kopie řetězcové argumenty, převod z formátu rozhraní .NET Framework (Unicode) do formátu nespravované platformy. Řetězce jsou neměnné a nebudou zkopírovány zpět z nespravované paměti spravované paměti při volání vrátí.  
  
 Následující tabulka uvádí možnosti zařazování pro řetězce při zařazené jako argument metody platformy vyvolat volání. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnoty výčtu k zařazování řetězců.  
  
|Typ výčtu|Popis nespravované formátu|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|COM – styl `BSTR` s předponou délku a ANSI znaků.|  
|`UnmanagedType.BStr`|COM – styl `BSTR` s předponou délku a znaky znakové sady Unicode.|  
|`UnmanagedType.LPStr`|Ukazatel pole znaků ANSI ukončené hodnotou null.|  
|`UnmanagedType.LPTStr`|Ukazatel na pole znaků závislé na platformu ukončené hodnotou null.|  
|`UnmanagedType.LPWStr`|Ukazatel na pole znaků Unicode ukončené hodnotou null.|  
|`UnmanagedType.TBStr`|COM – styl `BSTR` s předponou délku a závislé na platformě znaků.|  
|`VBByRefStr`|Hodnota, která umožňuje Visual Basic .NET, chcete-li změnit na řetězec v nespravovaného kódu a mít výsledky projeví ve spravovaném kódu. Tato hodnota je podporována pouze pro vyvolání platformy. Toto je výchozí hodnota v jazyce Visual Basic pro `ByVal` řetězce.|  
  
 Tato tabulka platí pro řetězce. Ale pro <xref:System.Text.StringBuilder>, jsou povoleny pouze možnosti `LPStr`, `LPTStr`, a `LPWStr`.  
  
 Následující definice typu ukazuje správné použití `MarshalAsAttribute` pro platformu vyvolat volání.  
  
```vb  
Class StringLibAPI      
Public Declare Auto Sub PassLPStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPStr)> s As String)      
Public Declare Auto Sub PassLPWStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPWStr)> s As String)      
Public Declare Auto Sub PassLPTStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPTStr)> s As String)      
Public Declare Auto Sub PassBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.BStr)> s As String)      
Public Declare Auto Sub PassAnsiBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.AnsiBStr)> s As String)      
Public Declare Auto Sub PassTBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.TBStr)> s As String)  
End Class  
```  
  
```csharp  
class StringLibAPI {  
[DllImport("StringLib.Dll")]  
public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPWStr([MarshalAs(UnmanagedType.LPWStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPTStr([MarshalAs(UnmanagedType.LPTStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)]  
String s);  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor2"></a>   
## <a name="strings-used-in-structures"></a>Řetězce použité v struktury  
 Řetězce jsou platné členové struktury; ale <xref:System.Text.StringBuilder> vyrovnávací paměti jsou neplatné v struktury. Následující tabulka zobrazuje zařazování možnosti pro datový typ řetězec, když je typ zařazené jako pole. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnoty výčtu k zařazování řetězců na pole.  
  
|Typ výčtu|Popis nespravované formátu|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|COM – styl `BSTR` s předponou délku a znaky znakové sady Unicode.|  
|`UnmanagedType.LPStr`|Ukazatel pole znaků ANSI ukončené hodnotou null.|  
|`UnmanagedType.LPTStr`|Ukazatel na pole znaků závislé na platformu ukončené hodnotou null.|  
|`UnmanagedType.LPWStr`|Ukazatel na pole znaků Unicode ukončené hodnotou null.|  
|`UnmanagedType.ByValTStr`|Pole pevnou délkou znaků; Typ tohoto pole je určena znaková sada obsahující struktury.|  
  
 `ByValTStr` Typ se používá pro vložené pevnou délkou znaková pole, které se zobrazují v rámci struktury. Jiné typy platí pro řetězec odkazy obsažené v struktury, které obsahují ukazatele na řetězce.  
  
 `CharSet` Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut, který se použije pro strukturu obsahující Určuje formát znakových řetězců v struktury. Následující příklad struktury obsahovat odkazy na řetězec a vložené řetězce, a také ANSI, kódování Unicode a závislé na platformě znaky.  
  
### <a name="type-library-representation"></a>Typ knihovny reprezentace  
  
```  
struct StringInfoA {  
   char *    f1;  
   char      f2[256];  
};  
struct StringInfoW {  
   WCHAR *   f1;  
   WCHAR     f2[256];  
   BSTR      f3;  
};  
struct StringInfoT {  
   TCHAR *   f1;  
   TCHAR     f2[256];  
};  
```  
  
 Následující příklad kódu ukazuje, jak používat <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut pro definování stejnou strukturu v různých formátech.  
  
```vb  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Ansi)> _  
Structure StringInfoA  
<MarshalAs(UnmanagedType.LPStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Unicode)> _  
Structure StringInfoW  
<MarshalAs(UnmanagedType.LPWStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
<MarshalAs(UnmanagedType.BStr)> Public f3 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Auto)> _  
Structure StringInfoT  
<MarshalAs(UnmanagedType.LPTStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Ansi)]  
struct StringInfoA {  
   [MarshalAs(UnmanagedType.LPStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Unicode)]  
struct StringInfoW {  
   [MarshalAs(UnmanagedType.LPWStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
   [MarshalAs(UnmanagedType.BStr)] public String f3;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Auto)]  
struct StringInfoT {  
   [MarshalAs(UnmanagedType.LPTStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor3"></a>   
## <a name="fixed-length-string-buffers"></a>Řetězce pevné délky vyrovnávací paměti  
 V některých případech vyrovnávací paměti pevné délky znak musí být předán do nespravovaného kódu do práce s. Jednoduše předávání řetězec nefunguje v tomto případě protože volaného nelze změnit obsah předané vyrovnávací paměti. I v případě, že řetězec je předán odkazem, neexistuje žádný způsob, jak inicializace vyrovnávací paměť na danou velikost.  
  
 Řešení je předat <xref:System.Text.StringBuilder> vyrovnávací paměti jako argument místo řetězec. A `StringBuilder` můžete přímo odkázat a upraveném volaného, pokud nepřesáhne kapacitu `StringBuilder`. Může být navíc inicializované na pevnou délkou. Například, pokud inicializaci `StringBuilder` vyrovnávací paměť pro kapacitou `N`, zařazování poskytuje vyrovnávací paměti o velikosti (`N`+ 1) znaků. Účty + 1 k tomu, že nespravované řetězec má hodnotu null. ukončovací při `StringBuilder` neexistuje.  
  
 Například rozhraní API Win32 Microsoft `GetWindowText` je znak pevnou délkou vyrovnávací paměť, která musí být předán do nespravovaného kódu manipulaci s těmito – funkce (definovanou v odkazující na Windows). `LpString`odkazuje na volající přidělit vyrovnávací paměť o velikosti `nMaxCount`. Volající musí přidělit vyrovnávací paměť a nastavte `nMaxCount` argument velikost přidělené vyrovnávací paměti. Následující kód ukazuje `GetWindowText` deklaraci funkce, jak jsou definovány v odkazující na Windows.  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 A `StringBuilder` můžete přímo odkázat a upraveném volaného, pokud nepřesáhne kapacitu `StringBuilder`. Následující příklad kódu ukazuje, jak `StringBuilder` jde inicializovat na pevnou délkou.  
  
```vb  
Public Class Win32API  
Public Declare Auto Sub GetWindowText Lib "User32.Dll" _  
(h As Integer, s As StringBuilder, nMaxCount As Integer)  
End Class  
Public Class Window  
   Friend h As Integer ' Friend handle to Window.  
   Public Function GetText() As String  
      Dim sb As New StringBuilder(256)  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1)  
   Return sb.ToString()  
   End Function  
End Class  
```  
  
```csharp  
public class Win32API {  
[DllImport("User32.Dll")]  
public static extern void GetWindowText(int h, StringBuilder s,   
int nMaxCount);  
}  
public class Window {  
   internal int h;        // Internal handle to Window.  
   public String GetText() {  
      StringBuilder sb = new StringBuilder(256);  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1);  
   return sb.ToString();  
   }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Výchozí chování zařazování](../../../docs/framework/interop/default-marshaling-behavior.md)  
 [Přenositelné a nepřenositelné typy](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [Směrovou atributy](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2)  
 [Kopírování a přichycování](../../../docs/framework/interop/copying-and-pinning.md)
