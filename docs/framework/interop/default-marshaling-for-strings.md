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
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="47799-102">Výchozí zařazování pro řetězce</span><span class="sxs-lookup"><span data-stu-id="47799-102">Default Marshaling for Strings</span></span>

<span data-ttu-id="47799-103">Třídy <xref:System.String?displayProperty=nameWithType> i <xref:System.Text.StringBuilder?displayProperty=nameWithType> mají podobné chování zařazování.</span><span class="sxs-lookup"><span data-stu-id="47799-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>

<span data-ttu-id="47799-104">Řetězce jsou zařazeny jako typ ve stylu `BSTR` com nebo jako řetězec zakončený hodnotou null (pole znaků, které končí znakem null).</span><span class="sxs-lookup"><span data-stu-id="47799-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="47799-105">Znaky v řetězci lze zařadit jako Unicode (výchozí v systémech Windows) nebo ANSI.</span><span class="sxs-lookup"><span data-stu-id="47799-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="47799-106">Řetězce používané v rozhraních</span><span class="sxs-lookup"><span data-stu-id="47799-106">Strings Used in Interfaces</span></span>

<span data-ttu-id="47799-107">V následující tabulce jsou uvedeny možnosti zařazování pro datový typ String při zařazení jako argument metody do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="47799-107">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="47799-108"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut poskytuje několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování řetězců do rozhraní com.</span><span class="sxs-lookup"><span data-stu-id="47799-108">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>

|<span data-ttu-id="47799-109">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="47799-109">Enumeration type</span></span>|<span data-ttu-id="47799-110">Popis nespravovaného formátu</span><span class="sxs-lookup"><span data-stu-id="47799-110">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="47799-111">`UnmanagedType.BStr`výchozí</span><span class="sxs-lookup"><span data-stu-id="47799-111">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="47799-112">Styl `BSTR` com s pevnou délkou a znaky kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="47799-112">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|`UnmanagedType.LPStr`|<span data-ttu-id="47799-113">Ukazatel na pole zakončené znakem null znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="47799-113">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="47799-114">Ukazatel na pole zakončené znakem null znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="47799-114">A pointer to a null-terminated array of Unicode characters.</span></span>|

<span data-ttu-id="47799-115">Tato tabulka platí pro <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="47799-115">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="47799-116"><xref:System.Text.StringBuilder>V případě je jediná možnost povolena `UnmanagedType.LPStr` a `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="47799-116">For <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>

<span data-ttu-id="47799-117">Následující příklad ukazuje řetězce deklarované v `IStringWorker` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="47799-117">The following example shows strings declared in the `IStringWorker` interface.</span></span>

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

<span data-ttu-id="47799-118">Následující příklad ukazuje odpovídající rozhraní popsané v knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="47799-118">The following example shows the corresponding interface described in a type library.</span></span>

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

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="47799-119">Řetězce používané při vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="47799-119">Strings Used in Platform Invoke</span></span>

<span data-ttu-id="47799-120">Vyvolání platformy kopíruje argumenty řetězce a převádí z formátu .NET Framework (Unicode) do nespravovaného formátu platformy.</span><span class="sxs-lookup"><span data-stu-id="47799-120">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="47799-121">Řetězce jsou neměnné a nejsou zkopírovány zpět z nespravované paměti do spravované paměti, když se volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="47799-121">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>

<span data-ttu-id="47799-122">V následující tabulce jsou uvedeny možnosti zařazování pro řetězce při zařazování jako argument metody volání platformy.</span><span class="sxs-lookup"><span data-stu-id="47799-122">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="47799-123"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut poskytuje několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování řetězců.</span><span class="sxs-lookup"><span data-stu-id="47799-123">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>

|<span data-ttu-id="47799-124">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="47799-124">Enumeration type</span></span>|<span data-ttu-id="47799-125">Popis nespravovaného formátu</span><span class="sxs-lookup"><span data-stu-id="47799-125">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="47799-126">Styl `BSTR` com s pevnou délkou a znaky ANSI.</span><span class="sxs-lookup"><span data-stu-id="47799-126">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|
|`UnmanagedType.BStr`|<span data-ttu-id="47799-127">Styl `BSTR` com s pevnou délkou a znaky kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="47799-127">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="47799-128">`UnmanagedType.LPStr`výchozí</span><span class="sxs-lookup"><span data-stu-id="47799-128">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="47799-129">Ukazatel na pole zakončené znakem null znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="47799-129">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="47799-130">Ukazatel na pole zakončené znakem null znaků závislých na platformě.</span><span class="sxs-lookup"><span data-stu-id="47799-130">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="47799-131">Ukazatel na pole zakončené znakem null v kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="47799-131">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="47799-132">Ukazatel na pole zakončené znakem null znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="47799-132">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.TBStr`|<span data-ttu-id="47799-133">Styl `BSTR` com s pevnou délkou a znaky závislé na platformě.</span><span class="sxs-lookup"><span data-stu-id="47799-133">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|
|`VBByRefStr`|<span data-ttu-id="47799-134">Hodnota, která umožňuje Visual Basic .NET změnit řetězec v nespravovaném kódu a výsledky se projeví ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="47799-134">A value that enables Visual Basic .NET to change a string in unmanaged code and have the results reflected in managed code.</span></span> <span data-ttu-id="47799-135">Tato hodnota je podporována pouze pro vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="47799-135">This value is supported only for platform invoke.</span></span> <span data-ttu-id="47799-136">Toto je výchozí hodnota v Visual Basic pro `ByVal` řetězce.</span><span class="sxs-lookup"><span data-stu-id="47799-136">This is the default value in Visual Basic for `ByVal` strings.</span></span>|

<span data-ttu-id="47799-137">Tato tabulka platí pro <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="47799-137">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="47799-138"><xref:System.Text.StringBuilder>V případě je jediná možnost povolena `LPStr`, `LPTStr`a `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="47799-138">For <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>

<span data-ttu-id="47799-139">Následující definice typu ukazuje správné použití `MarshalAsAttribute` pro volání vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="47799-139">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>

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

## <a name="strings-used-in-structures"></a><span data-ttu-id="47799-140">Řetězce používané ve strukturách</span><span class="sxs-lookup"><span data-stu-id="47799-140">Strings Used in Structures</span></span>

<span data-ttu-id="47799-141">Řetězce jsou platné členy struktur. <xref:System.Text.StringBuilder> vyrovnávací paměti jsou ale ve strukturách neplatné.</span><span class="sxs-lookup"><span data-stu-id="47799-141">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="47799-142">V následující tabulce jsou uvedeny možnosti zařazování pro <xref:System.String> datový typ při zařazení typu jako pole.</span><span class="sxs-lookup"><span data-stu-id="47799-142">The following table shows the marshaling options for the <xref:System.String> data type when the type is marshaled as a field.</span></span> <span data-ttu-id="47799-143"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut poskytuje několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování řetězců do pole.</span><span class="sxs-lookup"><span data-stu-id="47799-143">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>

|<span data-ttu-id="47799-144">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="47799-144">Enumeration type</span></span>|<span data-ttu-id="47799-145">Popis nespravovaného formátu</span><span class="sxs-lookup"><span data-stu-id="47799-145">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|<span data-ttu-id="47799-146">Styl `BSTR` com s pevnou délkou a znaky kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="47799-146">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="47799-147">`UnmanagedType.LPStr`výchozí</span><span class="sxs-lookup"><span data-stu-id="47799-147">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="47799-148">Ukazatel na pole zakončené znakem null znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="47799-148">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="47799-149">Ukazatel na pole zakončené znakem null znaků závislých na platformě.</span><span class="sxs-lookup"><span data-stu-id="47799-149">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="47799-150">Ukazatel na pole zakončené znakem null v kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="47799-150">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="47799-151">Ukazatel na pole zakončené znakem null znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="47799-151">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.ByValTStr`|<span data-ttu-id="47799-152">Pole znaků pevné délky; Typ pole je určen znakovou sadou obsahující struktury.</span><span class="sxs-lookup"><span data-stu-id="47799-152">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|

<span data-ttu-id="47799-153">`ByValTStr` Typ se používá pro vložená pole znaků s pevnou délkou, která se zobrazí v rámci struktury.</span><span class="sxs-lookup"><span data-stu-id="47799-153">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="47799-154">Další typy platí pro odkazy na řetězce obsažené ve strukturách, které obsahují ukazatele na řetězce.</span><span class="sxs-lookup"><span data-stu-id="47799-154">Other types apply to string references contained within structures that contain pointers to strings.</span></span>

<span data-ttu-id="47799-155">`CharSet` Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> , který je použit na obsahující strukturu, určuje formát znaků řetězců ve strukturách.</span><span class="sxs-lookup"><span data-stu-id="47799-155">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="47799-156">Následující ukázkové struktury obsahují odkazy na řetězce a vložené řetězce a také ANSI, Unicode a znaky závislé na platformě.</span><span class="sxs-lookup"><span data-stu-id="47799-156">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span> <span data-ttu-id="47799-157">Reprezentace těchto struktur v knihovně typů je uvedena v následujícím kódu jazyka C++:</span><span class="sxs-lookup"><span data-stu-id="47799-157">The representation of these structures in a type library is shown in the following C++ code:</span></span>

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

<span data-ttu-id="47799-158">Následující příklad ukazuje, jak použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> k definování stejné struktury v různých formátech.</span><span class="sxs-lookup"><span data-stu-id="47799-158">The following example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> to define the same structure in different formats.</span></span>

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

## <a name="fixed-length-string-buffers"></a><span data-ttu-id="47799-159">Vyrovnávací paměti pro řetězce s pevnou délkou</span><span class="sxs-lookup"><span data-stu-id="47799-159">Fixed-Length String Buffers</span></span>

<span data-ttu-id="47799-160">V některých případech musí být před manipulací do nespravovaného kódu předána vyrovnávací paměť znaků s pevnou délkou.</span><span class="sxs-lookup"><span data-stu-id="47799-160">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="47799-161">Pouhá předání řetězce v tomto případě nefunguje, protože volaný nemůže změnit obsah předané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="47799-161">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="47799-162">I v případě, že je řetězec předán odkazem, neexistuje způsob, jak vyrovnávací paměť inicializovat na danou velikost.</span><span class="sxs-lookup"><span data-stu-id="47799-162">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>

<span data-ttu-id="47799-163">Řešením je předání <xref:System.Text.StringBuilder> vyrovnávací paměti jako argumentu namísto <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="47799-163">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a <xref:System.String>.</span></span> <span data-ttu-id="47799-164">`StringBuilder` Může být zpětně prodána a upraveno volaným za předpokladu, že nepřekračuje kapacitu `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="47799-164">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="47799-165">Dá se taky inicializovat na pevnou délku.</span><span class="sxs-lookup"><span data-stu-id="47799-165">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="47799-166">Například Pokud inicializujete `StringBuilder` vyrovnávací paměť pro kapacitu `N`, zařazovací modul poskytuje vyrovnávací paměť o velikosti (`N`+ 1) znaků.</span><span class="sxs-lookup"><span data-stu-id="47799-166">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="47799-167">Účty + 1 pro skutečnost, že nespravovaný řetězec má ukončovací znak null, zatímco `StringBuilder` není.</span><span class="sxs-lookup"><span data-stu-id="47799-167">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>

<span data-ttu-id="47799-168">Například funkce rozhraní API systému [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) Windows (definovaná v *Winuser. h*) vyžaduje, aby volající předal vyrovnávací paměť znaků s pevnou délkou, do které funkce zapisuje text okna.</span><span class="sxs-lookup"><span data-stu-id="47799-168">For example, the Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API function (defined in *winuser.h*) requires that the caller pass a fixed-length character buffer to which the function writes the window's text.</span></span> <span data-ttu-id="47799-169">`LpString`odkazuje na velikost `nMaxCount`vyrovnávací paměti přidělené volajícímu.</span><span class="sxs-lookup"><span data-stu-id="47799-169">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="47799-170">Očekává se, že volající přidělí vyrovnávací paměť a nastaví `nMaxCount` argument na velikost přidělené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="47799-170">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="47799-171">Následující příklad ukazuje deklaraci `GetWindowText` funkce, jak je definováno v *Winuser. h*.</span><span class="sxs-lookup"><span data-stu-id="47799-171">The following example shows the `GetWindowText` function declaration as defined in *winuser.h*.</span></span>

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

<span data-ttu-id="47799-172">`StringBuilder` Může být zpětně prodána a upraveno volaným za předpokladu, že nepřekračuje kapacitu `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="47799-172">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="47799-173">Následující příklad kódu ukazuje, jak `StringBuilder` lze inicializovat s pevnou délkou.</span><span class="sxs-lookup"><span data-stu-id="47799-173">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="47799-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="47799-174">See also</span></span>

- [<span data-ttu-id="47799-175">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="47799-175">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="47799-176">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="47799-176">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="47799-177">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="47799-177">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="47799-178">[Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="47799-178">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="47799-179">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="47799-179">Copying and Pinning</span></span>](copying-and-pinning.md)
