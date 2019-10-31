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
ms.openlocfilehash: 49f2d871a42db484e20f0bfc35634a0e8b959c2e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123551"
---
# <a name="default-marshaling-for-strings"></a>Výchozí zařazování pro řetězce

Třídy <xref:System.String?displayProperty=nameWithType> i <xref:System.Text.StringBuilder?displayProperty=nameWithType> mají podobné chování při zařazování.

Řetězce jsou zařazeny jako typ `BSTR` ve stylu COM nebo jako řetězec zakončený hodnotou null (pole znaků, které končí znakem null). Znaky v řetězci lze zařadit jako Unicode (výchozí v systémech Windows) nebo ANSI.

## <a name="strings-used-in-interfaces"></a>Řetězce používané v rozhraních

V následující tabulce jsou uvedeny možnosti zařazování pro datový typ String při zařazení jako argument metody do nespravovaného kódu. Atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> poskytuje několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování řetězců do rozhraní COM.

|Typ výčtu|Popis nespravovaného formátu|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr` (výchozí)|`BSTR` ve stylu COM s pevnou délkou a znaky Unicode.|
|`UnmanagedType.LPStr`|Ukazatel na pole zakončené znakem null znaků ANSI.|
|`UnmanagedType.LPWStr`|Ukazatel na pole zakončené znakem null znaků Unicode.|

Tato tabulka se vztahuje na <xref:System.String>. Pro <xref:System.Text.StringBuilder>jsou jedinou povolenou možností `UnmanagedType.LPStr` a `UnmanagedType.LPWStr`.

Následující příklad ukazuje řetězce deklarované v rozhraní `IStringWorker`.

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

Následující příklad ukazuje odpovídající rozhraní popsané v knihovně typů.

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

## <a name="strings-used-in-platform-invoke"></a>Řetězce používané při vyvolání platformy

Vyvolání platformy kopíruje argumenty řetězce a převádí z formátu .NET Framework (Unicode) do nespravovaného formátu platformy. Řetězce jsou neměnné a nejsou zkopírovány zpět z nespravované paměti do spravované paměti, když se volání vrátí.

V následující tabulce jsou uvedeny možnosti zařazování pro řetězce při zařazování jako argument metody volání platformy. Atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> poskytuje několik hodnot <xref:System.Runtime.InteropServices.UnmanagedType> výčtu pro zařazování řetězců.

|Typ výčtu|Popis nespravovaného formátu|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|`BSTR` ve stylu COM s pevnou délkou a znaky ANSI.|
|`UnmanagedType.BStr`|`BSTR` ve stylu COM s pevnou délkou a znaky Unicode.|
|`UnmanagedType.LPStr` (výchozí)|Ukazatel na pole zakončené znakem null znaků ANSI.|
|`UnmanagedType.LPTStr`|Ukazatel na pole zakončené znakem null znaků závislých na platformě.|
|`UnmanagedType.LPUTF8Str`|Ukazatel na pole zakončené znakem null v kódování UTF-8.|
|`UnmanagedType.LPWStr`|Ukazatel na pole zakončené znakem null znaků Unicode.|
|`UnmanagedType.TBStr`|`BSTR` ve stylu COM s pevnou délkou a znaky závislé na platformě.|
|`VBByRefStr`|Hodnota, která umožňuje Visual Basic .NET změnit řetězec v nespravovaném kódu a výsledky se projeví ve spravovaném kódu. Tato hodnota je podporována pouze pro vyvolání platformy. Toto je výchozí hodnota v Visual Basic pro `ByVal` řetězce.|

Tato tabulka se vztahuje na <xref:System.String>. Pro <xref:System.Text.StringBuilder>jsou povolené jenom možnosti `LPStr`, `LPTStr`a `LPWStr`.

Následující definice typu ukazuje správné použití `MarshalAsAttribute` pro volání vyvolání platformy.

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

## <a name="strings-used-in-structures"></a>Řetězce používané ve strukturách

Řetězce jsou platné členy struktur. <xref:System.Text.StringBuilder> vyrovnávací paměti jsou však ve strukturách neplatné. V následující tabulce jsou uvedeny možnosti zařazování pro datový typ <xref:System.String>, když je typ zařazen jako pole. Atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> poskytuje několik hodnot <xref:System.Runtime.InteropServices.UnmanagedType> výčtu pro zařazování řetězců do pole.

|Typ výčtu|Popis nespravovaného formátu|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|`BSTR` ve stylu COM s pevnou délkou a znaky Unicode.|
|`UnmanagedType.LPStr` (výchozí)|Ukazatel na pole zakončené znakem null znaků ANSI.|
|`UnmanagedType.LPTStr`|Ukazatel na pole zakončené znakem null znaků závislých na platformě.|
|`UnmanagedType.LPUTF8Str`|Ukazatel na pole zakončené znakem null v kódování UTF-8.|
|`UnmanagedType.LPWStr`|Ukazatel na pole zakončené znakem null znaků Unicode.|
|`UnmanagedType.ByValTStr`|Pole znaků pevné délky; Typ pole je určen znakovou sadou obsahující struktury.|

Typ `ByValTStr` se používá pro vložená pole znaků s pevnou délkou, která se zobrazují v rámci struktury. Další typy platí pro odkazy na řetězce obsažené ve strukturách, které obsahují ukazatele na řetězce.

Argument `CharSet` <xref:System.Runtime.InteropServices.StructLayoutAttribute>, který je použit na obsaženou strukturu, určuje formát znaků řetězců ve strukturách. Následující ukázkové struktury obsahují odkazy na řetězce a vložené řetězce a také ANSI, Unicode a znaky závislé na platformě. Reprezentace těchto struktur v knihovně typů je uvedena v následujícím C++ kódu:

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

Následující příklad ukazuje, jak použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> k definování stejné struktury v různých formátech.

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

## <a name="fixed-length-string-buffers"></a>Vyrovnávací paměti pro řetězce s pevnou délkou

V některých případech musí být před manipulací do nespravovaného kódu předána vyrovnávací paměť znaků s pevnou délkou. Pouhá předání řetězce v tomto případě nefunguje, protože volaný nemůže změnit obsah předané vyrovnávací paměti. I v případě, že je řetězec předán odkazem, neexistuje způsob, jak vyrovnávací paměť inicializovat na danou velikost.

Řešením je předání <xref:System.Text.StringBuilder> vyrovnávací paměti jako argumentu namísto <xref:System.String>. `StringBuilder` lze odkázat a upravit volaným za předpokladu, že nepřekračuje kapacitu `StringBuilder`. Dá se taky inicializovat na pevnou délku. Například Pokud inicializujete vyrovnávací paměť `StringBuilder` do kapacity `N`, zařazovací modul poskytne velikost vyrovnávací paměti (`N`+ 1). Účty + 1 pro skutečnost, že nespravovaný řetězec má ukončovací znak null, když `StringBuilder` nepoužívá.

Například funkce rozhraní API pro Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) (definovaná v *Winuser. h*) vyžaduje, aby volající předal vyrovnávací paměť znaků s pevnou délkou, do které funkce zapisuje text okna. `LpString` odkazuje na vyrovnávací paměť přidělenou volajícímu `nMaxCount`velikosti. Očekává se, že volající přidělí vyrovnávací paměť a nastaví argument `nMaxCount` na velikost přidělené vyrovnávací paměti. Následující příklad ukazuje deklaraci funkce `GetWindowText`, jak je definováno v *Winuser. h*.

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

`StringBuilder` lze odkázat a upravit volaným za předpokladu, že nepřekračuje kapacitu `StringBuilder`. Následující příklad kódu ukazuje, jak lze `StringBuilder` inicializovat na pevnou délku.

```csharp
using System;
using System.Runtime.InteropServices;
using System.Text;

internal static class NativeMethods
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
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1);
        return sb.ToString();
    }
}
```

```vb
Imports System.Text

Friend Class NativeMethods
    Friend Declare Auto Sub GetWindowText Lib "User32.dll" _
        (hWnd As IntPtr, lpString As StringBuilder, nMaxCount As Integer)
End Class

Public Class Window
    Friend h As IntPtr ' Friend handle to Window.
    Public Function GetText() As String
        Dim sb As New StringBuilder(256)
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1)
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
