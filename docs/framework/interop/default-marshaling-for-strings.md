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
ms.openlocfilehash: df65f54a9a7408a22f8b558f99ab42d6c37ae55b
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221066"
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="6aeae-102">Výchozí zařazování pro řetězce</span><span class="sxs-lookup"><span data-stu-id="6aeae-102">Default Marshaling for Strings</span></span>
<span data-ttu-id="6aeae-103">Jak <xref:System.String?displayProperty=nameWithType> a <xref:System.Text.StringBuilder?displayProperty=nameWithType> třídy mají podobné chování zařazování.</span><span class="sxs-lookup"><span data-stu-id="6aeae-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>  
  
 <span data-ttu-id="6aeae-104">Řetězce, které jsou zařazeny jako stylu modelu COM. `BSTR` typu nebo jako řetězec zakončený hodnotou null (pole znaků, které končí znakem null).</span><span class="sxs-lookup"><span data-stu-id="6aeae-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="6aeae-105">Znaky v řetězci může být zařazována jako kódování Unicode (výchozí možnost v systémech Windows) nebo ANSI.</span><span class="sxs-lookup"><span data-stu-id="6aeae-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>  
  
 <span data-ttu-id="6aeae-106">Toto téma obsahuje následující informace o zařazování řetězcovými typy:</span><span class="sxs-lookup"><span data-stu-id="6aeae-106">This topic provides the following information on marshaling string types:</span></span>  
  
-   [<span data-ttu-id="6aeae-107">Řetězce použité v rozhraní</span><span class="sxs-lookup"><span data-stu-id="6aeae-107">Strings Used in Interfaces</span></span>](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [<span data-ttu-id="6aeae-108">Vyvolání řetězců použitých ve platformy</span><span class="sxs-lookup"><span data-stu-id="6aeae-108">Strings Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [<span data-ttu-id="6aeae-109">Řetězců použitých ve strukturách</span><span class="sxs-lookup"><span data-stu-id="6aeae-109">Strings Used in Structures</span></span>](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [<span data-ttu-id="6aeae-110">Vyrovnávací paměti pevné délky řetězců</span><span class="sxs-lookup"><span data-stu-id="6aeae-110">Fixed-Length String Buffers</span></span>](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="6aeae-111">Řetězce použité v rozhraní</span><span class="sxs-lookup"><span data-stu-id="6aeae-111">Strings Used in Interfaces</span></span>  
 <span data-ttu-id="6aeae-112">V následující tabulce jsou uvedeny možnosti zařazování pro datový typ string při zařazení jako argument metody nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="6aeae-112">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="6aeae-113"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování řetězců v modelu COM rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6aeae-113">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>  
  
|<span data-ttu-id="6aeae-114">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="6aeae-114">Enumeration type</span></span>|<span data-ttu-id="6aeae-115">Popis nespravované formátu</span><span class="sxs-lookup"><span data-stu-id="6aeae-115">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="6aeae-116">`UnmanagedType.BStr` (výchozí)</span><span class="sxs-lookup"><span data-stu-id="6aeae-116">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="6aeae-117">COM – styl `BSTR` s předponou délku a znaky kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="6aeae-117">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="6aeae-118">Ukazatel na pole zakončené znakem null znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="6aeae-118">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="6aeae-119">Ukazatel na pole zakončené znakem null znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="6aeae-119">A pointer to a null-terminated array of Unicode characters.</span></span>|  
  
 <span data-ttu-id="6aeae-120">Tato tabulka platí pro řetězce.</span><span class="sxs-lookup"><span data-stu-id="6aeae-120">This table applies to strings.</span></span> <span data-ttu-id="6aeae-121">Ale pro <xref:System.Text.StringBuilder>, jsou povolené jediné možnosti `UnmanagedType.LPStr` a `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="6aeae-121">However, for <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>  
  
 <span data-ttu-id="6aeae-122">Následující příklad ukazuje deklarované v řetězci `IStringWorker` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6aeae-122">The following example shows strings declared in the `IStringWorker` interface.</span></span>  
  
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

<span data-ttu-id="6aeae-123">Následující příklad ukazuje odpovídající rozhraní je popsáno v knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="6aeae-123">The following example shows the corresponding interface described in a type library.</span></span>

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

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="6aeae-124">Vyvolání řetězců použitých ve platformy</span><span class="sxs-lookup"><span data-stu-id="6aeae-124">Strings Used in Platform Invoke</span></span>  
 <span data-ttu-id="6aeae-125">Argumenty řetězce kopie, převod z formátu rozhraní .NET Framework (Unicode) do formátu nespravovaného platformu vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="6aeae-125">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="6aeae-126">Řetězce jsou neměnné a nejsou zkopírovány zpět z nespravované paměti pro spravované paměti při volání se vrátí.</span><span class="sxs-lookup"><span data-stu-id="6aeae-126">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>  
  
 <span data-ttu-id="6aeae-127">V následující tabulce jsou uvedeny možnosti zařazování pro řetězce při zařazení jako volání funkce invoke argumentu metody platformy.</span><span class="sxs-lookup"><span data-stu-id="6aeae-127">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="6aeae-128"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování řetězců v kódu.</span><span class="sxs-lookup"><span data-stu-id="6aeae-128">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>  
  
|<span data-ttu-id="6aeae-129">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="6aeae-129">Enumeration type</span></span>|<span data-ttu-id="6aeae-130">Popis nespravované formátu</span><span class="sxs-lookup"><span data-stu-id="6aeae-130">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="6aeae-131">COM – styl `BSTR` s předponou délku a znaky ANSI.</span><span class="sxs-lookup"><span data-stu-id="6aeae-131">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|  
|`UnmanagedType.BStr`|<span data-ttu-id="6aeae-132">COM – styl `BSTR` s předponou délku a znaky kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="6aeae-132">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="6aeae-133">Ukazatel na pole zakončené znakem null znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="6aeae-133">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="6aeae-134">Ukazatel na pole zakončené znakem null znaků závislého na platformě.</span><span class="sxs-lookup"><span data-stu-id="6aeae-134">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="6aeae-135">Ukazatel na pole zakončené znakem null znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="6aeae-135">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.TBStr`|<span data-ttu-id="6aeae-136">COM – styl `BSTR` s předponou délku a závislého na platformě znaků.</span><span class="sxs-lookup"><span data-stu-id="6aeae-136">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|  
|`VBByRefStr`|<span data-ttu-id="6aeae-137">Hodnota, která umožňuje Visual Basic .NET, chcete-li změnit řetězec v nespravovaných kódu a výsledky ve spravovaném kódu projeví.</span><span class="sxs-lookup"><span data-stu-id="6aeae-137">A value that enables Visual Basic .NET to change a string in unmanaged code, and have the results reflected in managed code.</span></span> <span data-ttu-id="6aeae-138">Tato hodnota je podporována pouze pro vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="6aeae-138">This value is supported only for platform invoke.</span></span> <span data-ttu-id="6aeae-139">Toto je výchozí hodnota v jazyce Visual Basic pro `ByVal` řetězce.</span><span class="sxs-lookup"><span data-stu-id="6aeae-139">This is default value in Visual Basic for `ByVal` strings.</span></span>|  
  
 <span data-ttu-id="6aeae-140">Tato tabulka platí pro řetězce.</span><span class="sxs-lookup"><span data-stu-id="6aeae-140">This table applies to strings.</span></span> <span data-ttu-id="6aeae-141">Ale pro <xref:System.Text.StringBuilder>, jsou povolené jediné možnosti `LPStr`, `LPTStr`, a `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="6aeae-141">However, for <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>  
  
 <span data-ttu-id="6aeae-142">Následující definice typu ukazuje správné použití `MarshalAsAttribute` voláními vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="6aeae-142">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>  
  
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
## <a name="strings-used-in-structures"></a><span data-ttu-id="6aeae-143">Řetězců použitých ve strukturách</span><span class="sxs-lookup"><span data-stu-id="6aeae-143">Strings Used in Structures</span></span>  
 <span data-ttu-id="6aeae-144">Řetězce jsou platných členů struktur; ale <xref:System.Text.StringBuilder> vyrovnávací paměti nejsou platné ve strukturách.</span><span class="sxs-lookup"><span data-stu-id="6aeae-144">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="6aeae-145">Následující tabulka uvádí možnosti zařazování pro datový typ string, když typ je zařazen jako pole.</span><span class="sxs-lookup"><span data-stu-id="6aeae-145">The following table shows the marshaling options for the string data type when the type is marshaled as a field.</span></span> <span data-ttu-id="6aeae-146"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> k zařazování řetězců na pole hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="6aeae-146">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>  
  
|<span data-ttu-id="6aeae-147">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="6aeae-147">Enumeration type</span></span>|<span data-ttu-id="6aeae-148">Popis nespravované formátu</span><span class="sxs-lookup"><span data-stu-id="6aeae-148">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|<span data-ttu-id="6aeae-149">COM – styl `BSTR` s předponou délku a znaky kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="6aeae-149">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="6aeae-150">Ukazatel na pole zakončené znakem null znaků ANSI.</span><span class="sxs-lookup"><span data-stu-id="6aeae-150">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="6aeae-151">Ukazatel na pole zakončené znakem null znaků závislého na platformě.</span><span class="sxs-lookup"><span data-stu-id="6aeae-151">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="6aeae-152">Ukazatel na pole zakončené znakem null znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="6aeae-152">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.ByValTStr`|<span data-ttu-id="6aeae-153">Pevné délky pole znaků; Typ pole je určeno znakovou sadu obsahující struktury.</span><span class="sxs-lookup"><span data-stu-id="6aeae-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|  
  
 <span data-ttu-id="6aeae-154">`ByValTStr` Typ se používá pro vložených polí znaků pevné délky, které se zobrazují v rámci struktury.</span><span class="sxs-lookup"><span data-stu-id="6aeae-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="6aeae-155">Jiné typy lze použít pro řetězec odkazů obsažených v rámci struktury, které obsahují ukazatele na řetězce.</span><span class="sxs-lookup"><span data-stu-id="6aeae-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>  
  
 <span data-ttu-id="6aeae-156">`CharSet` Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> Určuje atribut, který se použije na strukturu obsahující znak formátu řetězce ve strukturách.</span><span class="sxs-lookup"><span data-stu-id="6aeae-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="6aeae-157">Následující příklad struktury obsahují odkazy na řetězec a vložené řetězců, jakož i ANSI, Unicode a závislého na platformě znaků.</span><span class="sxs-lookup"><span data-stu-id="6aeae-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span>  
  
### <a name="type-library-representation"></a><span data-ttu-id="6aeae-158">Knihovna reprezentaci typu</span><span class="sxs-lookup"><span data-stu-id="6aeae-158">Type Library Representation</span></span>  
  
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
  
 <span data-ttu-id="6aeae-159">Následující příklad kódu ukazuje, jak používat <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut pro definování stejnou strukturu v různých formátech.</span><span class="sxs-lookup"><span data-stu-id="6aeae-159">The following code example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to define the same structure in different formats.</span></span>  
  
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
## <a name="fixed-length-string-buffers"></a><span data-ttu-id="6aeae-160">Vyrovnávací paměti pevné délky řetězců</span><span class="sxs-lookup"><span data-stu-id="6aeae-160">Fixed-Length String Buffers</span></span>  
 <span data-ttu-id="6aeae-161">Za určitých okolností znaků pevné délky vyrovnávací paměti musí předávat do nespravovaného kódu na manipulovat.</span><span class="sxs-lookup"><span data-stu-id="6aeae-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="6aeae-162">Jednoduše předáním řetězce nelze použít v tomto případě vzhledem k tomu, že volaný nelze změnit obsah předanou vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="6aeae-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="6aeae-163">I v případě, že řetězec je předána odkazem, neexistuje žádný způsob, jak inicializovat na danou velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6aeae-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>  
  
 <span data-ttu-id="6aeae-164">Řešením je předat <xref:System.Text.StringBuilder> vyrovnávací paměti jako argument namísto řetězce.</span><span class="sxs-lookup"><span data-stu-id="6aeae-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a string.</span></span> <span data-ttu-id="6aeae-165">A `StringBuilder` lze přistoupit přes ukazatel a upravit volaným, pokud nepřekročí kapacitu `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="6aeae-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="6aeae-166">Můžete být navíc inicializované na pevnou délku.</span><span class="sxs-lookup"><span data-stu-id="6aeae-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="6aeae-167">Například, pokud je inicializovat `StringBuilder` vyrovnávací paměť kapacitu `N`, aby zařazování odvozovalo poskytuje vyrovnávací paměť o velikosti (`N`+ 1) znaků.</span><span class="sxs-lookup"><span data-stu-id="6aeae-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="6aeae-168">Účty + 1 pro skutečnost, že nespravovaný řetězec má ukončovací znak null při `StringBuilder` tak není.</span><span class="sxs-lookup"><span data-stu-id="6aeae-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>  
  
 <span data-ttu-id="6aeae-169">Například rozhraní Microsoft Win32 API `GetWindowText` – funkce (definováno v Windows.h) je znaků pevné délky vyrovnávací paměť, která musí být předán do nespravovaného kódu na manipulovat.</span><span class="sxs-lookup"><span data-stu-id="6aeae-169">For example, the Microsoft Win32 API `GetWindowText` function (defined in Windows.h) is a fixed-length character buffer that must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="6aeae-170">`LpString` odkazuje na volající – přidělené vyrovnávací paměti o velikosti `nMaxCount`.</span><span class="sxs-lookup"><span data-stu-id="6aeae-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="6aeae-171">Očekává se volající přidělení vyrovnávací paměti a nastavit `nMaxCount` argument velikost přidělené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6aeae-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="6aeae-172">Následující kód ukazuje `GetWindowText` deklaraci funkce, jak jsou definovány v Windows.h.</span><span class="sxs-lookup"><span data-stu-id="6aeae-172">The following code shows the `GetWindowText` function declaration as defined in Windows.h.</span></span>  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 <span data-ttu-id="6aeae-173">A `StringBuilder` lze přistoupit přes ukazatel a upravit volaným, pokud nepřekročí kapacitu `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="6aeae-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="6aeae-174">Následující příklad kódu ukazuje, jak `StringBuilder` mohou být inicializovány na pevnou délku.</span><span class="sxs-lookup"><span data-stu-id="6aeae-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6aeae-175">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6aeae-175">See also</span></span>
- [<span data-ttu-id="6aeae-176">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="6aeae-176">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="6aeae-177">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="6aeae-177">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="6aeae-178">[Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6aeae-178">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="6aeae-179">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="6aeae-179">Copying and Pinning</span></span>](copying-and-pinning.md)
