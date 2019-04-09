---
title: Výchozí zařazování pro řetězce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47543056eaa538b008db3332dda776c0f300108d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078466"
---
# <a name="default-marshaling-for-strings"></a>Výchozí zařazování pro řetězce
Jak <xref:System.String?displayProperty=nameWithType> a <xref:System.Text.StringBuilder?displayProperty=nameWithType> třídy mají podobné chování zařazování.  
  
 Řetězce, které jsou zařazeny jako stylu modelu COM. `BSTR` typu nebo jako řetězec zakončený hodnotou null (pole znaků, které končí znakem null). Znaky v řetězci může být zařazována jako kódování Unicode (výchozí možnost v systémech Windows) nebo ANSI.  
  
 Toto téma obsahuje následující informace o zařazování řetězcovými typy:  
  
-   [Řetězce použité v rozhraní](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [Vyvolání řetězců použitých ve platformy](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [Řetězců použitých ve strukturách](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [Vyrovnávací paměti pevné délky řetězců](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>

## <a name="strings-used-in-interfaces"></a>Řetězce použité v rozhraní  
 V následující tabulce jsou uvedeny možnosti zařazování pro datový typ string při zařazení jako argument metody nespravovaného kódu. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování řetězců v modelu COM rozhraní.  
  
|Typ výčtu|Popis nespravované formátu|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr` (výchozí)|COM – styl `BSTR` s předponou délku a znaky kódování Unicode.|  
|`UnmanagedType.LPStr`|Ukazatel na pole zakončené znakem null znaků ANSI.|  
|`UnmanagedType.LPWStr`|Ukazatel na pole zakončené znakem null znaků Unicode.|  
  
 Tato tabulka platí pro řetězce. Ale pro <xref:System.Text.StringBuilder>, jsou povolené jediné možnosti `UnmanagedType.LPStr` a `UnmanagedType.LPWStr`.  
  
 Následující příklad ukazuje deklarované v řetězci `IStringWorker` rozhraní.  
  
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

Následující příklad ukazuje odpovídající rozhraní je popsáno v knihovně typů.

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

## <a name="strings-used-in-platform-invoke"></a>Vyvolání řetězců použitých ve platformy  
 Argumenty řetězce kopie, převod z formátu rozhraní .NET Framework (Unicode) do formátu nespravovaného platformu vyvolání platformy. Řetězce jsou neměnné a nejsou zkopírovány zpět z nespravované paměti pro spravované paměti při volání se vrátí.  
  
 V následující tabulce jsou uvedeny možnosti zařazování pro řetězce při zařazení jako volání funkce invoke argumentu metody platformy. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování řetězců v kódu.  
  
|Typ výčtu|Popis nespravované formátu|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|COM – styl `BSTR` s předponou délku a znaky ANSI.|  
|`UnmanagedType.BStr`|COM – styl `BSTR` s předponou délku a znaky kódování Unicode.|  
|`UnmanagedType.LPStr`|Ukazatel na pole zakončené znakem null znaků ANSI.|  
|`UnmanagedType.LPTStr`|Ukazatel na pole zakončené znakem null znaků závislého na platformě.|  
|`UnmanagedType.LPWStr`|Ukazatel na pole zakončené znakem null znaků Unicode.|  
|`UnmanagedType.TBStr`|COM – styl `BSTR` s předponou délku a závislého na platformě znaků.|  
|`VBByRefStr`|Hodnota, která umožňuje Visual Basic .NET, chcete-li změnit řetězec v nespravovaných kódu a výsledky ve spravovaném kódu projeví. Tato hodnota je podporována pouze pro vyvolání platformy. Toto je výchozí hodnota v jazyce Visual Basic pro `ByVal` řetězce.|  
  
 Tato tabulka platí pro řetězce. Ale pro <xref:System.Text.StringBuilder>, jsou povolené jediné možnosti `LPStr`, `LPTStr`, a `LPWStr`.  
  
 Následující definice typu ukazuje správné použití `MarshalAsAttribute` voláními vyvolání platformy.  
  
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
## <a name="strings-used-in-structures"></a>Řetězců použitých ve strukturách  
 Řetězce jsou platných členů struktur; ale <xref:System.Text.StringBuilder> vyrovnávací paměti nejsou platné ve strukturách. Následující tabulka uvádí možnosti zařazování pro datový typ string, když typ je zařazen jako pole. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> k zařazování řetězců na pole hodnot výčtu.  
  
|Typ výčtu|Popis nespravované formátu|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|COM – styl `BSTR` s předponou délku a znaky kódování Unicode.|  
|`UnmanagedType.LPStr`|Ukazatel na pole zakončené znakem null znaků ANSI.|  
|`UnmanagedType.LPTStr`|Ukazatel na pole zakončené znakem null znaků závislého na platformě.|  
|`UnmanagedType.LPWStr`|Ukazatel na pole zakončené znakem null znaků Unicode.|  
|`UnmanagedType.ByValTStr`|Pevné délky pole znaků; Typ pole je určeno znakovou sadu obsahující struktury.|  
  
 `ByValTStr` Typ se používá pro vložených polí znaků pevné délky, které se zobrazují v rámci struktury. Jiné typy lze použít pro řetězec odkazů obsažených v rámci struktury, které obsahují ukazatele na řetězce.  
  
 `CharSet` Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> Určuje atribut, který se použije na strukturu obsahující znak formátu řetězce ve strukturách. Následující příklad struktury obsahují odkazy na řetězec a vložené řetězců, jakož i ANSI, Unicode a závislého na platformě znaků.  
  
### <a name="type-library-representation"></a>Knihovna reprezentaci typu  
  
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
## <a name="fixed-length-string-buffers"></a>Vyrovnávací paměti pevné délky řetězců  
 Za určitých okolností znaků pevné délky vyrovnávací paměti musí předávat do nespravovaného kódu na manipulovat. Jednoduše předáním řetězce nelze použít v tomto případě vzhledem k tomu, že volaný nelze změnit obsah předanou vyrovnávací paměť. I v případě, že řetězec je předána odkazem, neexistuje žádný způsob, jak inicializovat na danou velikost vyrovnávací paměti.  
  
 Řešením je předat <xref:System.Text.StringBuilder> vyrovnávací paměti jako argument namísto řetězce. A `StringBuilder` lze přistoupit přes ukazatel a upravit volaným, pokud nepřekročí kapacitu `StringBuilder`. Můžete být navíc inicializované na pevnou délku. Například, pokud je inicializovat `StringBuilder` vyrovnávací paměť kapacitu `N`, aby zařazování odvozovalo poskytuje vyrovnávací paměť o velikosti (`N`+ 1) znaků. Účty + 1 pro skutečnost, že nespravovaný řetězec má ukončovací znak null při `StringBuilder` tak není.  
  
 Například rozhraní API Microsoft Windows `GetWindowText` – funkce (definováno v Windows.h) je znaků pevné délky vyrovnávací paměť, která musí být předán do nespravovaného kódu na manipulovat. `LpString` odkazuje na volající – přidělené vyrovnávací paměti o velikosti `nMaxCount`. Očekává se volající přidělení vyrovnávací paměti a nastavit `nMaxCount` argument velikost přidělené vyrovnávací paměti. Následující kód ukazuje `GetWindowText` deklaraci funkce, jak jsou definovány v Windows.h.  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 A `StringBuilder` lze přistoupit přes ukazatel a upravit volaným, pokud nepřekročí kapacitu `StringBuilder`. Následující příklad kódu ukazuje, jak `StringBuilder` mohou být inicializovány na pevnou délku.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Výchozí chování zařazování](default-marshaling-behavior.md)
- [Přenositelné a nepřenositelné typy](blittable-and-non-blittable-types.md)
- [Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopírování a přichycování](copying-and-pinning.md)
