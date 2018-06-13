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
ms.openlocfilehash: 88604058bd460d80214be6051abef7dc561c7710
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394904"
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="3167b-102">Výchozí zařazování pro řetězce</span><span class="sxs-lookup"><span data-stu-id="3167b-102">Default Marshaling for Strings</span></span>
<span data-ttu-id="3167b-103">Jak <xref:System.String?displayProperty=nameWithType> a <xref:System.Text.StringBuilder?displayProperty=nameWithType> třídy mají podobné chování zařazování.</span><span class="sxs-lookup"><span data-stu-id="3167b-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>  
  
 <span data-ttu-id="3167b-104">Řetězce jsou zařazené jako stylu COM `BSTR` typu nebo jako řetězce ukončené hodnotou null (pole znaků, který končí znak hodnoty null).</span><span class="sxs-lookup"><span data-stu-id="3167b-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="3167b-105">Můžete zařadit znaky v řetězci, jako kódování Unicode (výchozí nastavení v systémech Windows) nebo ANSI.</span><span class="sxs-lookup"><span data-stu-id="3167b-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>  
  
 <span data-ttu-id="3167b-106">Toto téma obsahuje následující informace na zařazování typů řetězec:</span><span class="sxs-lookup"><span data-stu-id="3167b-106">This topic provides the following information on marshaling string types:</span></span>  
  
-   [<span data-ttu-id="3167b-107">Řetězce používané v rozhraních</span><span class="sxs-lookup"><span data-stu-id="3167b-107">Strings Used in Interfaces</span></span>](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [<span data-ttu-id="3167b-108">Vyvolání řetězce použité v platformě</span><span class="sxs-lookup"><span data-stu-id="3167b-108">Strings Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [<span data-ttu-id="3167b-109">Řetězce použité v struktury</span><span class="sxs-lookup"><span data-stu-id="3167b-109">Strings Used in Structures</span></span>](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [<span data-ttu-id="3167b-110">Řetězce pevné délky vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="3167b-110">Fixed-Length String Buffers</span></span>](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="3167b-111">Řetězce používané v rozhraních</span><span class="sxs-lookup"><span data-stu-id="3167b-111">Strings Used in Interfaces</span></span>  
 <span data-ttu-id="3167b-112">V následující tabulce jsou uvedeny možnosti zařazování pro datový typ řetězec při zařazené jako argument metody na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="3167b-112">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="3167b-113"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnoty výčtu k zařazování řetězců do rozhraní COM.</span><span class="sxs-lookup"><span data-stu-id="3167b-113">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>  
  
|<span data-ttu-id="3167b-114">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="3167b-114">Enumeration type</span></span>|<span data-ttu-id="3167b-115">Popis nespravované formátu</span><span class="sxs-lookup"><span data-stu-id="3167b-115">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="3167b-116">`UnmanagedType.BStr` (výchozí)</span><span class="sxs-lookup"><span data-stu-id="3167b-116">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="3167b-117">COM – styl `BSTR` s předponou délku a znaky znakové sady Unicode.</span><span class="sxs-lookup"><span data-stu-id="3167b-117">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="3167b-118">Ukazatel pole znaků ANSI ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="3167b-118">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="3167b-119">Ukazatel na pole znaků Unicode ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="3167b-119">A pointer to a null-terminated array of Unicode characters.</span></span>|  
  
 <span data-ttu-id="3167b-120">Tato tabulka platí pro řetězce.</span><span class="sxs-lookup"><span data-stu-id="3167b-120">This table applies to strings.</span></span> <span data-ttu-id="3167b-121">Ale pro <xref:System.Text.StringBuilder>, jsou povoleny pouze možnosti `UnmanagedType.LPStr` a `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="3167b-121">However, for <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>  
  
 <span data-ttu-id="3167b-122">Následující příklad ukazuje řetězce v deklarována `IStringWorker` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3167b-122">The following example shows strings declared in the `IStringWorker` interface.</span></span>  
  
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

<span data-ttu-id="3167b-123">Následující příklad ukazuje odpovídající rozhraní, které jsou popsané v knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="3167b-123">The following example shows the corresponding interface described in a type library.</span></span>

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

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="3167b-124">Vyvolání řetězce použité v platformě</span><span class="sxs-lookup"><span data-stu-id="3167b-124">Strings Used in Platform Invoke</span></span>  
 <span data-ttu-id="3167b-125">Vyvolání platformy kopie řetězcové argumenty, převod z formátu rozhraní .NET Framework (Unicode) do formátu nespravované platformy.</span><span class="sxs-lookup"><span data-stu-id="3167b-125">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="3167b-126">Řetězce jsou neměnné a nebudou zkopírovány zpět z nespravované paměti spravované paměti při volání vrátí.</span><span class="sxs-lookup"><span data-stu-id="3167b-126">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>  
  
 <span data-ttu-id="3167b-127">Následující tabulka uvádí možnosti zařazování pro řetězce při zařazené jako argument metody platformy vyvolat volání.</span><span class="sxs-lookup"><span data-stu-id="3167b-127">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="3167b-128"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnoty výčtu k zařazování řetězců.</span><span class="sxs-lookup"><span data-stu-id="3167b-128">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>  
  
|<span data-ttu-id="3167b-129">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="3167b-129">Enumeration type</span></span>|<span data-ttu-id="3167b-130">Popis nespravované formátu</span><span class="sxs-lookup"><span data-stu-id="3167b-130">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="3167b-131">COM – styl `BSTR` s předponou délku a ANSI znaků.</span><span class="sxs-lookup"><span data-stu-id="3167b-131">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|  
|`UnmanagedType.BStr`|<span data-ttu-id="3167b-132">COM – styl `BSTR` s předponou délku a znaky znakové sady Unicode.</span><span class="sxs-lookup"><span data-stu-id="3167b-132">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="3167b-133">Ukazatel pole znaků ANSI ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="3167b-133">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="3167b-134">Ukazatel na pole znaků závislé na platformu ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="3167b-134">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="3167b-135">Ukazatel na pole znaků Unicode ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="3167b-135">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.TBStr`|<span data-ttu-id="3167b-136">COM – styl `BSTR` s předponou délku a závislé na platformě znaků.</span><span class="sxs-lookup"><span data-stu-id="3167b-136">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|  
|`VBByRefStr`|<span data-ttu-id="3167b-137">Hodnota, která umožňuje Visual Basic .NET, chcete-li změnit na řetězec v nespravovaného kódu a mít výsledky projeví ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="3167b-137">A value that enables Visual Basic .NET to change a string in unmanaged code, and have the results reflected in managed code.</span></span> <span data-ttu-id="3167b-138">Tato hodnota je podporována pouze pro vyvolání platformy.</span><span class="sxs-lookup"><span data-stu-id="3167b-138">This value is supported only for platform invoke.</span></span> <span data-ttu-id="3167b-139">Toto je výchozí hodnota v jazyce Visual Basic pro `ByVal` řetězce.</span><span class="sxs-lookup"><span data-stu-id="3167b-139">This is default value in Visual Basic for `ByVal` strings.</span></span>|  
  
 <span data-ttu-id="3167b-140">Tato tabulka platí pro řetězce.</span><span class="sxs-lookup"><span data-stu-id="3167b-140">This table applies to strings.</span></span> <span data-ttu-id="3167b-141">Ale pro <xref:System.Text.StringBuilder>, jsou povoleny pouze možnosti `LPStr`, `LPTStr`, a `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="3167b-141">However, for <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>  
  
 <span data-ttu-id="3167b-142">Následující definice typu ukazuje správné použití `MarshalAsAttribute` pro platformu vyvolat volání.</span><span class="sxs-lookup"><span data-stu-id="3167b-142">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>  
  
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
## <a name="strings-used-in-structures"></a><span data-ttu-id="3167b-143">Řetězce použité v struktury</span><span class="sxs-lookup"><span data-stu-id="3167b-143">Strings Used in Structures</span></span>  
 <span data-ttu-id="3167b-144">Řetězce jsou platné členové struktury; ale <xref:System.Text.StringBuilder> vyrovnávací paměti jsou neplatné v struktury.</span><span class="sxs-lookup"><span data-stu-id="3167b-144">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="3167b-145">Následující tabulka zobrazuje zařazování možnosti pro datový typ řetězec, když je typ zařazené jako pole.</span><span class="sxs-lookup"><span data-stu-id="3167b-145">The following table shows the marshaling options for the string data type when the type is marshaled as a field.</span></span> <span data-ttu-id="3167b-146"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnoty výčtu k zařazování řetězců na pole.</span><span class="sxs-lookup"><span data-stu-id="3167b-146">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>  
  
|<span data-ttu-id="3167b-147">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="3167b-147">Enumeration type</span></span>|<span data-ttu-id="3167b-148">Popis nespravované formátu</span><span class="sxs-lookup"><span data-stu-id="3167b-148">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|<span data-ttu-id="3167b-149">COM – styl `BSTR` s předponou délku a znaky znakové sady Unicode.</span><span class="sxs-lookup"><span data-stu-id="3167b-149">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="3167b-150">Ukazatel pole znaků ANSI ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="3167b-150">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="3167b-151">Ukazatel na pole znaků závislé na platformu ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="3167b-151">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="3167b-152">Ukazatel na pole znaků Unicode ukončené hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="3167b-152">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.ByValTStr`|<span data-ttu-id="3167b-153">Pole pevnou délkou znaků; Typ tohoto pole je určena znaková sada obsahující struktury.</span><span class="sxs-lookup"><span data-stu-id="3167b-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|  
  
 <span data-ttu-id="3167b-154">`ByValTStr` Typ se používá pro vložené pevnou délkou znaková pole, které se zobrazují v rámci struktury.</span><span class="sxs-lookup"><span data-stu-id="3167b-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="3167b-155">Jiné typy platí pro řetězec odkazy obsažené v struktury, které obsahují ukazatele na řetězce.</span><span class="sxs-lookup"><span data-stu-id="3167b-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>  
  
 <span data-ttu-id="3167b-156">`CharSet` Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut, který se použije pro strukturu obsahující Určuje formát znakových řetězců v struktury.</span><span class="sxs-lookup"><span data-stu-id="3167b-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="3167b-157">Následující příklad struktury obsahovat odkazy na řetězec a vložené řetězce, a také ANSI, kódování Unicode a závislé na platformě znaky.</span><span class="sxs-lookup"><span data-stu-id="3167b-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span>  
  
### <a name="type-library-representation"></a><span data-ttu-id="3167b-158">Typ knihovny reprezentace</span><span class="sxs-lookup"><span data-stu-id="3167b-158">Type Library Representation</span></span>  
  
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
  
 <span data-ttu-id="3167b-159">Následující příklad kódu ukazuje, jak používat <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut pro definování stejnou strukturu v různých formátech.</span><span class="sxs-lookup"><span data-stu-id="3167b-159">The following code example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to define the same structure in different formats.</span></span>  
  
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
## <a name="fixed-length-string-buffers"></a><span data-ttu-id="3167b-160">Řetězce pevné délky vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="3167b-160">Fixed-Length String Buffers</span></span>  
 <span data-ttu-id="3167b-161">V některých případech vyrovnávací paměti pevné délky znak musí být předán do nespravovaného kódu do práce s.</span><span class="sxs-lookup"><span data-stu-id="3167b-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="3167b-162">Jednoduše předávání řetězec nefunguje v tomto případě protože volaného nelze změnit obsah předané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="3167b-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="3167b-163">I v případě, že řetězec je předán odkazem, neexistuje žádný způsob, jak inicializace vyrovnávací paměť na danou velikost.</span><span class="sxs-lookup"><span data-stu-id="3167b-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>  
  
 <span data-ttu-id="3167b-164">Řešení je předat <xref:System.Text.StringBuilder> vyrovnávací paměti jako argument místo řetězec.</span><span class="sxs-lookup"><span data-stu-id="3167b-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a string.</span></span> <span data-ttu-id="3167b-165">A `StringBuilder` můžete přímo odkázat a upraveném volaného, pokud nepřesáhne kapacitu `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="3167b-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="3167b-166">Může být navíc inicializované na pevnou délkou.</span><span class="sxs-lookup"><span data-stu-id="3167b-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="3167b-167">Například, pokud inicializaci `StringBuilder` vyrovnávací paměť pro kapacitou `N`, zařazování poskytuje vyrovnávací paměti o velikosti (`N`+ 1) znaků.</span><span class="sxs-lookup"><span data-stu-id="3167b-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="3167b-168">Účty + 1 k tomu, že nespravované řetězec má hodnotu null. ukončovací při `StringBuilder` neexistuje.</span><span class="sxs-lookup"><span data-stu-id="3167b-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>  
  
 <span data-ttu-id="3167b-169">Například rozhraní API Win32 Microsoft `GetWindowText` je znak pevnou délkou vyrovnávací paměť, která musí být předán do nespravovaného kódu manipulaci s těmito – funkce (definovanou v odkazující na Windows).</span><span class="sxs-lookup"><span data-stu-id="3167b-169">For example, the Microsoft Win32 API `GetWindowText` function (defined in Windows.h) is a fixed-length character buffer that must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="3167b-170">`LpString` odkazuje na volající přidělit vyrovnávací paměť o velikosti `nMaxCount`.</span><span class="sxs-lookup"><span data-stu-id="3167b-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="3167b-171">Volající musí přidělit vyrovnávací paměť a nastavte `nMaxCount` argument velikost přidělené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="3167b-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="3167b-172">Následující kód ukazuje `GetWindowText` deklaraci funkce, jak jsou definovány v odkazující na Windows.</span><span class="sxs-lookup"><span data-stu-id="3167b-172">The following code shows the `GetWindowText` function declaration as defined in Windows.h.</span></span>  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 <span data-ttu-id="3167b-173">A `StringBuilder` můžete přímo odkázat a upraveném volaného, pokud nepřesáhne kapacitu `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="3167b-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="3167b-174">Následující příklad kódu ukazuje, jak `StringBuilder` jde inicializovat na pevnou délkou.</span><span class="sxs-lookup"><span data-stu-id="3167b-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3167b-175">Viz také</span><span class="sxs-lookup"><span data-stu-id="3167b-175">See Also</span></span>  
 [<span data-ttu-id="3167b-176">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="3167b-176">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)  
 [<span data-ttu-id="3167b-177">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="3167b-177">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)  
 <span data-ttu-id="3167b-178">[Směrovou atributy](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3167b-178">[Directional Attributes](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span></span>  
 [<span data-ttu-id="3167b-179">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="3167b-179">Copying and Pinning</span></span>](copying-and-pinning.md)
