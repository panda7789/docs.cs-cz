---
title: Výchozí zařazování pro řetězce
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c07747c5100f6f7b7ee80b2e7e39d22362698e4
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807834"
---
# <a name="default-marshaling-for-strings"></a>Výchozí zařazování pro řetězce

Jak <xref:System.String?displayProperty=nameWithType> a <xref:System.Text.StringBuilder?displayProperty=nameWithType> třídy mají podobné chování zařazování.

Řetězce, které jsou zařazeny jako stylu modelu COM. `BSTR` typu nebo jako řetězec zakončený hodnotou null (pole znaků, které končí znakem null). Znaky v řetězci může být zařazována jako kódování Unicode (výchozí možnost v systémech Windows) nebo ANSI.

## <a name="strings-used-in-interfaces"></a>Řetězce použité v rozhraní

V následující tabulce jsou uvedeny možnosti zařazování pro datový typ string při zařazení jako argument metody nespravovaného kódu. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování řetězců v modelu COM rozhraní.

|Typ výčtu|Popis nespravované formátu|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr` (výchozí)|COM – styl `BSTR` s předponou délku a znaky kódování Unicode.|
|`UnmanagedType.LPStr`|Ukazatel na pole zakončené znakem null znaků ANSI.|
|`UnmanagedType.LPWStr`|Ukazatel na pole zakončené znakem null znaků Unicode.|

Tato tabulka platí pro <xref:System.String>. Pro <xref:System.Text.StringBuilder>, jsou povolené jediné možnosti `UnmanagedType.LPStr` a `UnmanagedType.LPWStr`.

Následující příklad ukazuje deklarované v řetězci `IStringWorker` rozhraní.

```csharp
public interface IStringWorker
{
    void PassString1(string s);
    void PassString2([MarshalAs(UnmanagedType.BStr)] string s);
    void PassString3([MarshalAs(UnmanagedType.LPStr)] string s);
    void PassString4([MarshalAs(UnmanagedType.LPWStr)] string s);
    void PassStringRef1(ref string s);
    void PassStringRef2([MarshalAs(UnmanagedType.BStr)] ref string s);
    void PassStringRef3([MarshalAs(UnmanagedType.LPStr)] ref string s);
    void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)] ref string s);
}
```

```vb
Public Interface IStringWorker
    Sub PassString1(s As String)
    Sub PassString2(<MarshalAs(UnmanagedType.BStr)> s As String)
    Sub PassString3(<MarshalAs(UnmanagedType.LPStr)> s As String)
    Sub PassString4(<MarshalAs(UnmanagedType.LPWStr)> s As String)
    Sub PassStringRef1(ByRef s As String)
    Sub PassStringRef2(<MarshalAs(UnmanagedType.BStr)> ByRef s As String)
    Sub PassStringRef3(<MarshalAs(UnmanagedType.LPStr)> ByRef s As String)
    Sub PassStringRef4(<MarshalAs(UnmanagedType.LPWStr)> ByRef s As String)
End Interface
```

Následující příklad ukazuje odpovídající rozhraní je popsáno v knihovně typů.

```cpp
interface IStringWorker : IDispatch
{
    HRESULT PassString1([in] BSTR s);
    HRESULT PassString2([in] BSTR s);
    HRESULT PassString3([in] LPStr s);
    HRESULT PassString4([in] LPWStr s);
    HRESULT PassStringRef1([in, out] BSTR *s);
    HRESULT PassStringRef2([in, out] BSTR *s);
    HRESULT PassStringRef3([in, out] LPStr *s);
    HRESULT PassStringRef4([in, out] LPWStr *s);
};
```

## <a name="strings-used-in-platform-invoke"></a>Vyvolání řetězců použitých ve platformy

Argumenty řetězce kopie, převod z formátu rozhraní .NET Framework (Unicode) do formátu nespravovaného platformu vyvolání platformy. Řetězce jsou neměnné a nejsou zkopírovány zpět z nespravované paměti pro spravované paměti při volání se vrátí.

V následující tabulce jsou uvedeny možnosti zařazování pro řetězce při zařazení jako volání funkce invoke argumentu metody platformy. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování řetězců v kódu.

|Typ výčtu|Popis nespravované formátu|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|COM – styl `BSTR` s předponou délku a znaky ANSI.|
|`UnmanagedType.BStr`|COM – styl `BSTR` s předponou délku a znaky kódování Unicode.|
|`UnmanagedType.LPStr` (výchozí)|Ukazatel na pole zakončené znakem null znaků ANSI.|
|`UnmanagedType.LPTStr`|Ukazatel na pole zakončené znakem null znaků závislého na platformě.|
|`UnmanagedType.LPUTF8Str`|Ukazatel na pole zakončené znakem null UTF-8 kódování znaků.|
|`UnmanagedType.LPWStr`|Ukazatel na pole zakončené znakem null znaků Unicode.|
|`UnmanagedType.TBStr`|COM – styl `BSTR` s předponou délku a závislého na platformě znaků.|
|`VBByRefStr`|Hodnota, která umožňuje Visual Basic .NET, chcete-li změnit řetězec v nespravovaných kódu a výsledky ve spravovaném kódu projeví. Tato hodnota je podporována pouze pro vyvolání platformy. Jedná se o výchozí hodnotu v jazyce Visual Basic pro `ByVal` řetězce.|

Tato tabulka platí pro <xref:System.String>. Pro <xref:System.Text.StringBuilder>, jsou povolené jediné možnosti `LPStr`, `LPTStr`, a `LPWStr`.

Následující definice typu ukazuje správné použití `MarshalAsAttribute` voláními vyvolání platformy.

```csharp
class StringLibAPI
{
    [DllImport("StringLib.dll")]
    public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPWStr([MarshalAs(UnmanagedType.LPWStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPTStr([MarshalAs(UnmanagedType.LPTStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPUTF8Str([MarshalAs(UnmanagedType.LPUTF8Str)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)] string s);
}
```

```vb
Class StringLibAPI
    Public Declare Auto Sub PassLPStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPStr)> s As String)
    Public Declare Auto Sub PassLPWStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPWStr)> s As String)
    Public Declare Auto Sub PassLPTStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPTStr)> s As String)
    Public Declare Auto Sub PassLPUTF8Str Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPUTF8Str)> s As String)
    Public Declare Auto Sub PassBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.BStr)> s As String)
    Public Declare Auto Sub PassAnsiBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.AnsiBStr)> s As String)
    Public Declare Auto Sub PassTBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.TBStr)> s As String)
End Class
```

## <a name="strings-used-in-structures"></a>Řetězců použitých ve strukturách

Řetězce jsou platných členů struktur; ale <xref:System.Text.StringBuilder> vyrovnávací paměti nejsou platné ve strukturách. V následující tabulce jsou uvedeny možnosti zařazování pro <xref:System.String> datového typu, když typ je zařazen jako pole. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> k zařazování řetězců na pole hodnot výčtu.

|Typ výčtu|Popis nespravované formátu|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|COM – styl `BSTR` s předponou délku a znaky kódování Unicode.|
|`UnmanagedType.LPStr` (výchozí)|Ukazatel na pole zakončené znakem null znaků ANSI.|
|`UnmanagedType.LPTStr`|Ukazatel na pole zakončené znakem null znaků závislého na platformě.|
|`UnmanagedType.LPUTF8Str`|Ukazatel na pole zakončené znakem null UTF-8 kódování znaků.|
|`UnmanagedType.LPWStr`|Ukazatel na pole zakončené znakem null znaků Unicode.|
|`UnmanagedType.ByValTStr`|Pevné délky pole znaků; Typ pole je určeno znakovou sadu obsahující struktury.|

`ByValTStr` Typ se používá pro vložených polí znaků pevné délky, které se zobrazují v rámci struktury. Jiné typy lze použít pro řetězec odkazů obsažených v rámci struktury, které obsahují ukazatele na řetězce.

`CharSet` Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> , která je použita na obsahující struktura Určuje znak formátu řetězce ve strukturách. Následující příklad struktury obsahují odkazy na řetězec a vložené řetězců, jakož i ANSI, Unicode a závislého na platformě znaků. Reprezentace těchto struktur v knihovně typů je znázorněno v následujícím C++ kódu:

```cpp
struct StringInfoA
{
    char *  f1;
    char    f2[256];
};

struct StringInfoW
{
    WCHAR * f1;
    WCHAR   f2[256];
    BSTR    f3;
};

struct StringInfoT
{
    TCHAR * f1;
    TCHAR   f2[256];
};
```

Následující příklad ukazuje způsob použití <xref:System.Runtime.InteropServices.MarshalAsAttribute> k definování stejnou strukturu v různých formátech.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
struct StringInfoA
{
    [MarshalAs(UnmanagedType.LPStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
struct StringInfoW
{
    [MarshalAs(UnmanagedType.LPWStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
    [MarshalAs(UnmanagedType.BStr)] public string f3;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Auto)]
struct StringInfoT
{
    [MarshalAs(UnmanagedType.LPTStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}
```

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

## <a name="fixed-length-string-buffers"></a>Vyrovnávací paměti pevné délky řetězců

Za určitých okolností znaků pevné délky vyrovnávací paměti musí předávat do nespravovaného kódu na manipulovat. Jednoduše předáním řetězce nelze použít v tomto případě vzhledem k tomu, že volaný nelze změnit obsah předanou vyrovnávací paměť. I v případě, že řetězec je předána odkazem, neexistuje žádný způsob, jak inicializovat na danou velikost vyrovnávací paměti.

Řešením je předat <xref:System.Text.StringBuilder> vyrovnávací paměti jako argument místo <xref:System.String>. A `StringBuilder` lze přistoupit přes ukazatel a upravit volaným, pokud nepřekročí kapacitu `StringBuilder`. Můžete být navíc inicializované na pevnou délku. Například, pokud je inicializovat `StringBuilder` vyrovnávací paměť kapacitu `N`, aby zařazování odvozovalo poskytuje vyrovnávací paměť o velikosti (`N`+ 1) znaků. Účty + 1 pro skutečnost, že nespravovaný řetězec má ukončovací znak null při `StringBuilder` tak není.

Například Windows [ `GetWindowText` ](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) – funkce rozhraní API (definované v *Windows.h*) vyžaduje, aby volající předat do vyrovnávací paměti znaků pevné délky, ke kterému tato funkce zapíše text okna. `LpString` odkazuje na volající – přidělené vyrovnávací paměti o velikosti `nMaxCount`. Očekává se volající přidělení vyrovnávací paměti a nastavit `nMaxCount` argument velikost přidělené vyrovnávací paměti. Následující příklad ukazuje `GetWindowText` deklaraci funkce, jak jsou definovány v *Windows.h*.

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

A `StringBuilder` lze přistoupit přes ukazatel a upravit volaným, pokud nepřekročí kapacitu `StringBuilder`. Následující příklad kódu ukazuje, jak `StringBuilder` mohou být inicializovány na pevnou délku.

```csharp
internal static class WindowsAPI
{
    [DllImport("User32.dll")]
    internal static extern void GetWindowText(IntPtr hWnd, StringBuilder lpString, int nMaxCount);
}

public class Window
{
    internal IntPtr h;        // Internal handle to Window.
    public String GetText()
    {
        StringBuilder sb = new StringBuilder(256);
        WindowsAPI.GetWindowText(h, sb, sb.Capacity + 1);
        return sb.ToString();
    }
}
```

```vb
Friend Class WindowsAPI
    Friend Shared Declare Auto Sub GetWindowText Lib "User32.dll" _
        (hWnd As IntPtr, lpString As StringBuilder, nMaxCount As Integer)
End Class

Public Class Window
    Friend h As IntPtr ' Friend handle to Window.
    Public Function GetText() As String
        Dim sb As New StringBuilder(256)
        WindowsAPI.GetWindowText(h, sb, sb.Capacity + 1)
        Return sb.ToString()
   End Function
End Class
```

## <a name="see-also"></a>Viz také:

- [Výchozí chování zařazování](default-marshaling-behavior.md)
- [Zařazování řetězců](marshaling-strings.md)
- [Přenositelné a nepřenositelné typy](blittable-and-non-blittable-types.md)
- [Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopírování a přichycování](copying-and-pinning.md)
