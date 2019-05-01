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
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="6bced-102">Výchozí zařazování pro řetězce</span><span class="sxs-lookup"><span data-stu-id="6bced-102">Default Marshaling for Strings</span></span>

<span data-ttu-id="6bced-103">Jak <xref:System.String?displayProperty=nameWithType> a <xref:System.Text.StringBuilder?displayProperty=nameWithType> třídy mají podobné chování zařazování.</span><span class="sxs-lookup"><span data-stu-id="6bced-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>

<span data-ttu-id="6bced-104">Řetězce, které jsou zařazeny jako stylu modelu COM. `BSTR` typu nebo jako řetězec zakončený hodnotou null (pole znaků, které končí znakem null).</span><span class="sxs-lookup"><span data-stu-id="6bced-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="6bced-105">Znaky v řetězci může být zařazována jako kódování Unicode (výchozí možnost v systémech Windows) nebo ANSI.</span><span class="sxs-lookup"><span data-stu-id="6bced-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="6bced-106">Řetězce použité v rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bced-106">Strings Used in Interfaces</span></span>

<span data-ttu-id="6bced-107">V následující tabulce jsou uvedeny možnosti zařazování pro datový typ string při zařazení jako argument metody nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6bced-107">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="6bced-108"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování řetězců v modelu COM rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6bced-108">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>

|<span data-ttu-id="6bced-109">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="6bced-109">Enumeration type</span></span>|<span data-ttu-id="6bced-110">Popis nespravované formátu</span><span class="sxs-lookup"><span data-stu-id="6bced-110">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="6bced-111">`UnmanagedType.BStr` (výchozí)</span><span class="sxs-lookup"><span data-stu-id="6bced-111">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="6bced-112">COM – styl `BSTR` s předponou délku a znaky kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="6bced-112">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|`UnmanagedType.LPStr`|<span data-ttu-id="6bced-113">Ukazatel na pole zakončené znakem null znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="6bced-113">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="6bced-114">Ukazatel na pole zakončené znakem null znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="6bced-114">A pointer to a null-terminated array of Unicode characters.</span></span>|

<span data-ttu-id="6bced-115">Tato tabulka platí pro <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="6bced-115">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="6bced-116">Pro <xref:System.Text.StringBuilder>, jsou povolené jediné možnosti `UnmanagedType.LPStr` a `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="6bced-116">For <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>

<span data-ttu-id="6bced-117">Následující příklad ukazuje deklarované v řetězci `IStringWorker` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6bced-117">The following example shows strings declared in the `IStringWorker` interface.</span></span>

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

<span data-ttu-id="6bced-118">Následující příklad ukazuje odpovídající rozhraní je popsáno v knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="6bced-118">The following example shows the corresponding interface described in a type library.</span></span>

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

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="6bced-119">Vyvolání řetězců použitých ve platformy</span><span class="sxs-lookup"><span data-stu-id="6bced-119">Strings Used in Platform Invoke</span></span>

<span data-ttu-id="6bced-120">Argumenty řetězce kopie, převod z formátu rozhraní .NET Framework (Unicode) do formátu nespravovaného platformu vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="6bced-120">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="6bced-121">Řetězce jsou neměnné a nejsou zkopírovány zpět z nespravované paměti pro spravované paměti při volání se vrátí.</span><span class="sxs-lookup"><span data-stu-id="6bced-121">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>

<span data-ttu-id="6bced-122">V následující tabulce jsou uvedeny možnosti zařazování pro řetězce při zařazení jako volání funkce invoke argumentu metody platformy.</span><span class="sxs-lookup"><span data-stu-id="6bced-122">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="6bced-123"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování řetězců v kódu.</span><span class="sxs-lookup"><span data-stu-id="6bced-123">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>

|<span data-ttu-id="6bced-124">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="6bced-124">Enumeration type</span></span>|<span data-ttu-id="6bced-125">Popis nespravované formátu</span><span class="sxs-lookup"><span data-stu-id="6bced-125">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="6bced-126">COM – styl `BSTR` s předponou délku a znaky ANSI.</span><span class="sxs-lookup"><span data-stu-id="6bced-126">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|
|`UnmanagedType.BStr`|<span data-ttu-id="6bced-127">COM – styl `BSTR` s předponou délku a znaky kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="6bced-127">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="6bced-128">`UnmanagedType.LPStr` (výchozí)</span><span class="sxs-lookup"><span data-stu-id="6bced-128">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="6bced-129">Ukazatel na pole zakončené znakem null znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="6bced-129">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="6bced-130">Ukazatel na pole zakončené znakem null znaků závislého na platformě.</span><span class="sxs-lookup"><span data-stu-id="6bced-130">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="6bced-131">Ukazatel na pole zakončené znakem null UTF-8 kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="6bced-131">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="6bced-132">Ukazatel na pole zakončené znakem null znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="6bced-132">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.TBStr`|<span data-ttu-id="6bced-133">COM – styl `BSTR` s předponou délku a závislého na platformě znaků.</span><span class="sxs-lookup"><span data-stu-id="6bced-133">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|
|`VBByRefStr`|<span data-ttu-id="6bced-134">Hodnota, která umožňuje Visual Basic .NET, chcete-li změnit řetězec v nespravovaných kódu a výsledky ve spravovaném kódu projeví.</span><span class="sxs-lookup"><span data-stu-id="6bced-134">A value that enables Visual Basic .NET to change a string in unmanaged code and have the results reflected in managed code.</span></span> <span data-ttu-id="6bced-135">Tato hodnota je podporována pouze pro vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="6bced-135">This value is supported only for platform invoke.</span></span> <span data-ttu-id="6bced-136">Jedná se o výchozí hodnotu v jazyce Visual Basic pro `ByVal` řetězce.</span><span class="sxs-lookup"><span data-stu-id="6bced-136">This is the default value in Visual Basic for `ByVal` strings.</span></span>|

<span data-ttu-id="6bced-137">Tato tabulka platí pro <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="6bced-137">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="6bced-138">Pro <xref:System.Text.StringBuilder>, jsou povolené jediné možnosti `LPStr`, `LPTStr`, a `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="6bced-138">For <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>

<span data-ttu-id="6bced-139">Následující definice typu ukazuje správné použití `MarshalAsAttribute` voláními vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="6bced-139">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>

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

## <a name="strings-used-in-structures"></a><span data-ttu-id="6bced-140">Řetězců použitých ve strukturách</span><span class="sxs-lookup"><span data-stu-id="6bced-140">Strings Used in Structures</span></span>

<span data-ttu-id="6bced-141">Řetězce jsou platných členů struktur; ale <xref:System.Text.StringBuilder> vyrovnávací paměti nejsou platné ve strukturách.</span><span class="sxs-lookup"><span data-stu-id="6bced-141">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="6bced-142">V následující tabulce jsou uvedeny možnosti zařazování pro <xref:System.String> datového typu, když typ je zařazen jako pole.</span><span class="sxs-lookup"><span data-stu-id="6bced-142">The following table shows the marshaling options for the <xref:System.String> data type when the type is marshaled as a field.</span></span> <span data-ttu-id="6bced-143"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> k zařazování řetězců na pole hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="6bced-143">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>

|<span data-ttu-id="6bced-144">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="6bced-144">Enumeration type</span></span>|<span data-ttu-id="6bced-145">Popis nespravované formátu</span><span class="sxs-lookup"><span data-stu-id="6bced-145">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|<span data-ttu-id="6bced-146">COM – styl `BSTR` s předponou délku a znaky kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="6bced-146">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="6bced-147">`UnmanagedType.LPStr` (výchozí)</span><span class="sxs-lookup"><span data-stu-id="6bced-147">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="6bced-148">Ukazatel na pole zakončené znakem null znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="6bced-148">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="6bced-149">Ukazatel na pole zakončené znakem null znaků závislého na platformě.</span><span class="sxs-lookup"><span data-stu-id="6bced-149">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="6bced-150">Ukazatel na pole zakončené znakem null UTF-8 kódování znaků.</span><span class="sxs-lookup"><span data-stu-id="6bced-150">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="6bced-151">Ukazatel na pole zakončené znakem null znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="6bced-151">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.ByValTStr`|<span data-ttu-id="6bced-152">Pevné délky pole znaků; Typ pole je určeno znakovou sadu obsahující struktury.</span><span class="sxs-lookup"><span data-stu-id="6bced-152">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|

<span data-ttu-id="6bced-153">`ByValTStr` Typ se používá pro vložených polí znaků pevné délky, které se zobrazují v rámci struktury.</span><span class="sxs-lookup"><span data-stu-id="6bced-153">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="6bced-154">Jiné typy lze použít pro řetězec odkazů obsažených v rámci struktury, které obsahují ukazatele na řetězce.</span><span class="sxs-lookup"><span data-stu-id="6bced-154">Other types apply to string references contained within structures that contain pointers to strings.</span></span>

<span data-ttu-id="6bced-155">`CharSet` Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> , která je použita na obsahující struktura Určuje znak formátu řetězce ve strukturách.</span><span class="sxs-lookup"><span data-stu-id="6bced-155">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="6bced-156">Následující příklad struktury obsahují odkazy na řetězec a vložené řetězců, jakož i ANSI, Unicode a závislého na platformě znaků.</span><span class="sxs-lookup"><span data-stu-id="6bced-156">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span> <span data-ttu-id="6bced-157">Reprezentace těchto struktur v knihovně typů je znázorněno v následujícím C++ kódu:</span><span class="sxs-lookup"><span data-stu-id="6bced-157">The representation of these structures in a type library is shown in the following C++ code:</span></span>

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

<span data-ttu-id="6bced-158">Následující příklad ukazuje způsob použití <xref:System.Runtime.InteropServices.MarshalAsAttribute> k definování stejnou strukturu v různých formátech.</span><span class="sxs-lookup"><span data-stu-id="6bced-158">The following example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> to define the same structure in different formats.</span></span>

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

## <a name="fixed-length-string-buffers"></a><span data-ttu-id="6bced-159">Vyrovnávací paměti pevné délky řetězců</span><span class="sxs-lookup"><span data-stu-id="6bced-159">Fixed-Length String Buffers</span></span>

<span data-ttu-id="6bced-160">Za určitých okolností znaků pevné délky vyrovnávací paměti musí předávat do nespravovaného kódu na manipulovat.</span><span class="sxs-lookup"><span data-stu-id="6bced-160">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="6bced-161">Jednoduše předáním řetězce nelze použít v tomto případě vzhledem k tomu, že volaný nelze změnit obsah předanou vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="6bced-161">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="6bced-162">I v případě, že řetězec je předána odkazem, neexistuje žádný způsob, jak inicializovat na danou velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6bced-162">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>

<span data-ttu-id="6bced-163">Řešením je předat <xref:System.Text.StringBuilder> vyrovnávací paměti jako argument místo <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="6bced-163">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a <xref:System.String>.</span></span> <span data-ttu-id="6bced-164">A `StringBuilder` lze přistoupit přes ukazatel a upravit volaným, pokud nepřekročí kapacitu `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="6bced-164">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="6bced-165">Můžete být navíc inicializované na pevnou délku.</span><span class="sxs-lookup"><span data-stu-id="6bced-165">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="6bced-166">Například, pokud je inicializovat `StringBuilder` vyrovnávací paměť kapacitu `N`, aby zařazování odvozovalo poskytuje vyrovnávací paměť o velikosti (`N`+ 1) znaků.</span><span class="sxs-lookup"><span data-stu-id="6bced-166">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="6bced-167">Účty + 1 pro skutečnost, že nespravovaný řetězec má ukončovací znak null při `StringBuilder` tak není.</span><span class="sxs-lookup"><span data-stu-id="6bced-167">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>

<span data-ttu-id="6bced-168">Například Windows [ `GetWindowText` ](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) – funkce rozhraní API (definované v *Windows.h*) vyžaduje, aby volající předat do vyrovnávací paměti znaků pevné délky, ke kterému tato funkce zapíše text okna.</span><span class="sxs-lookup"><span data-stu-id="6bced-168">For example, the Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API function (defined in *Windows.h*) requires that the caller pass a fixed-length character buffer to which the function writes the window's text.</span></span> <span data-ttu-id="6bced-169">`LpString` odkazuje na volající – přidělené vyrovnávací paměti o velikosti `nMaxCount`.</span><span class="sxs-lookup"><span data-stu-id="6bced-169">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="6bced-170">Očekává se volající přidělení vyrovnávací paměti a nastavit `nMaxCount` argument velikost přidělené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6bced-170">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="6bced-171">Následující příklad ukazuje `GetWindowText` deklaraci funkce, jak jsou definovány v *Windows.h*.</span><span class="sxs-lookup"><span data-stu-id="6bced-171">The following example shows the `GetWindowText` function declaration as defined in *Windows.h*.</span></span>

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

<span data-ttu-id="6bced-172">A `StringBuilder` lze přistoupit přes ukazatel a upravit volaným, pokud nepřekročí kapacitu `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="6bced-172">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="6bced-173">Následující příklad kódu ukazuje, jak `StringBuilder` mohou být inicializovány na pevnou délku.</span><span class="sxs-lookup"><span data-stu-id="6bced-173">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6bced-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6bced-174">See also</span></span>

- [<span data-ttu-id="6bced-175">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="6bced-175">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="6bced-176">Zařazování řetězců</span><span class="sxs-lookup"><span data-stu-id="6bced-176">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="6bced-177">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="6bced-177">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="6bced-178">[Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6bced-178">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="6bced-179">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="6bced-179">Copying and Pinning</span></span>](copying-and-pinning.md)
