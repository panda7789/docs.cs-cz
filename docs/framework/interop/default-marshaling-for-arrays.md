---
title: Výchozí zařazování pro pole
description: Pochopte Výchozí zařazování pro pole. Zkontrolujte spravovaná pole, nespravovaná pole, předávání parametrů pole do kódu .NET a předávání polí do modelu COM.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
ms.openlocfilehash: eafed0e0a0150923aae0fa68a1b96e6d9d66b07a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622559"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="a3025-104">Výchozí zařazování pro pole</span><span class="sxs-lookup"><span data-stu-id="a3025-104">Default Marshaling for Arrays</span></span>
<span data-ttu-id="a3025-105">V aplikaci, která se skládá výhradně ze spravovaného kódu, modul common language runtime předá typy polí jako vstupně-výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="a3025-105">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="a3025-106">Naproti tomu zařazovací modul Interop předá pole jako parametry ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="a3025-106">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="a3025-107">S [optimalizací připnutí](copying-and-pinning.md)se může při interakci s objekty ve stejném objektu Apartment zdát, že se jako parametr v/v funguje přenositelná pole.</span><span class="sxs-lookup"><span data-stu-id="a3025-107">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="a3025-108">Nicméně pokud později exportujete kód do knihovny typů, která se používá k vygenerování mezipočítačového proxy serveru, a tato knihovna slouží k zařazování volání napříč objekty Apartment, volání se mohou vrátit na hodnotu true v chování parametrů.</span><span class="sxs-lookup"><span data-stu-id="a3025-108">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="a3025-109">Pole jsou složitá podle povahy a rozdíly mezi spravovanými a nespravovanými poli opravňují více informací než jiné nepřenositelné typy.</span><span class="sxs-lookup"><span data-stu-id="a3025-109">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span>  
  
## <a name="managed-arrays"></a><span data-ttu-id="a3025-110">Spravovaná pole</span><span class="sxs-lookup"><span data-stu-id="a3025-110">Managed Arrays</span></span>  
 <span data-ttu-id="a3025-111">Typy spravovaných polí se mohou lišit. <xref:System.Array?displayProperty=nameWithType>Třída je však základní třídou všech typů polí.</span><span class="sxs-lookup"><span data-stu-id="a3025-111">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="a3025-112">Třída **System. Array** má vlastnosti pro určení pořadí, délky a dolních a horních mezí pole a také metod pro přístup, řazení, hledání, kopírování a vytváření polí.</span><span class="sxs-lookup"><span data-stu-id="a3025-112">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="a3025-113">Tyto typy polí jsou dynamické a nemají odpovídající statický typ definovaný v knihovně základních tříd.</span><span class="sxs-lookup"><span data-stu-id="a3025-113">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="a3025-114">Je vhodné si představit každou kombinaci typu prvku a seřadit jako odlišný typ pole.</span><span class="sxs-lookup"><span data-stu-id="a3025-114">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="a3025-115">Proto jednorozměrné pole celých čísel je jiného typu než jednorozměrné pole typu Double.</span><span class="sxs-lookup"><span data-stu-id="a3025-115">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="a3025-116">Podobně dvourozměrné pole celých čísel je jiné než jednorozměrné pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="a3025-116">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="a3025-117">Hranice pole se při porovnávání typů neberou v potaz.</span><span class="sxs-lookup"><span data-stu-id="a3025-117">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="a3025-118">Jak ukazuje následující tabulka, jakákoli instance spravovaného pole musí být konkrétního typu prvku, pořadí a dolní mez.</span><span class="sxs-lookup"><span data-stu-id="a3025-118">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="a3025-119">Typ spravovaného pole</span><span class="sxs-lookup"><span data-stu-id="a3025-119">Managed array type</span></span>|<span data-ttu-id="a3025-120">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="a3025-120">Element type</span></span>|<span data-ttu-id="a3025-121">Rank</span><span class="sxs-lookup"><span data-stu-id="a3025-121">Rank</span></span>|<span data-ttu-id="a3025-122">Dolní mez</span><span class="sxs-lookup"><span data-stu-id="a3025-122">Lower bound</span></span>|<span data-ttu-id="a3025-123">Zápis signatury</span><span class="sxs-lookup"><span data-stu-id="a3025-123">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="a3025-124">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="a3025-124">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="a3025-125">Zadáno podle typu.</span><span class="sxs-lookup"><span data-stu-id="a3025-125">Specified by type.</span></span>|<span data-ttu-id="a3025-126">Určeno podle pořadí.</span><span class="sxs-lookup"><span data-stu-id="a3025-126">Specified by rank.</span></span>|<span data-ttu-id="a3025-127">Volitelně určené hranicemi.</span><span class="sxs-lookup"><span data-stu-id="a3025-127">Optionally specified by bounds.</span></span>|<span data-ttu-id="a3025-128">*typ* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="a3025-128">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="a3025-129">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="a3025-129">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="a3025-130">Není známo</span><span class="sxs-lookup"><span data-stu-id="a3025-130">Unknown</span></span>|<span data-ttu-id="a3025-131">Není známo</span><span class="sxs-lookup"><span data-stu-id="a3025-131">Unknown</span></span>|<span data-ttu-id="a3025-132">Není známo</span><span class="sxs-lookup"><span data-stu-id="a3025-132">Unknown</span></span>|<span data-ttu-id="a3025-133">**System. Array**</span><span class="sxs-lookup"><span data-stu-id="a3025-133">**System.Array**</span></span>|  
|<span data-ttu-id="a3025-134">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="a3025-134">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="a3025-135">Zadáno podle typu.</span><span class="sxs-lookup"><span data-stu-id="a3025-135">Specified by type.</span></span>|<span data-ttu-id="a3025-136">1</span><span class="sxs-lookup"><span data-stu-id="a3025-136">1</span></span>|<span data-ttu-id="a3025-137">0</span><span class="sxs-lookup"><span data-stu-id="a3025-137">0</span></span>|<span data-ttu-id="a3025-138">*typ* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="a3025-138">*type* **[** *n* **]**</span></span>|  
  
## <a name="unmanaged-arrays"></a><span data-ttu-id="a3025-139">Nespravovaná pole</span><span class="sxs-lookup"><span data-stu-id="a3025-139">Unmanaged Arrays</span></span>  
 <span data-ttu-id="a3025-140">Nespravovaná pole jsou buď bezpečná pole ve stylu COM, nebo pole ve stylu jazyka C s pevnou nebo proměnnou délkou.</span><span class="sxs-lookup"><span data-stu-id="a3025-140">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="a3025-141">Bezpečná pole jsou samy popisující pole, která přenesou typ, pořadí a meze přidružených dat pole.</span><span class="sxs-lookup"><span data-stu-id="a3025-141">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="a3025-142">Pole stylu C jsou jednorozměrná typová pole s pevně nastavenou dolní mezí 0.</span><span class="sxs-lookup"><span data-stu-id="a3025-142">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="a3025-143">Zařazovací služba má omezené podpory pro oba typy polí.</span><span class="sxs-lookup"><span data-stu-id="a3025-143">The marshaling service has limited support for both types of arrays.</span></span>  
  
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="a3025-144">Předávání parametrů pole do kódu .NET</span><span class="sxs-lookup"><span data-stu-id="a3025-144">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="a3025-145">Pole stylu C a bezpečná pole mohou být předány do kódu .NET z nespravovaného kódu jako bezpečné pole nebo pole ve stylu jazyka C.</span><span class="sxs-lookup"><span data-stu-id="a3025-145">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="a3025-146">Následující tabulka ukazuje nespravovaný typ hodnoty a importovaný typ.</span><span class="sxs-lookup"><span data-stu-id="a3025-146">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="a3025-147">Nespravovaný typ</span><span class="sxs-lookup"><span data-stu-id="a3025-147">Unmanaged type</span></span>|<span data-ttu-id="a3025-148">Importovaný typ</span><span class="sxs-lookup"><span data-stu-id="a3025-148">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="a3025-149">**SAFEARRAY (** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="a3025-149">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="a3025-150">**ELEMENT_TYPE_SZARRAY\*\*\*\*\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="a3025-150">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="a3025-151">Rank = 1, dolní mez = 0.</span><span class="sxs-lookup"><span data-stu-id="a3025-151">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="a3025-152">Velikost je známá pouze v případě, že je k dispozici ve spravovaném podpisu.</span><span class="sxs-lookup"><span data-stu-id="a3025-152">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="a3025-153">Bezpečná pole, která nejsou pořadí = 1 nebo dolní mez = 0, nelze zařadit jako **SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="a3025-153">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="a3025-154">*Typ*  **[]**</span><span class="sxs-lookup"><span data-stu-id="a3025-154">*Type*  **[]**</span></span>|<span data-ttu-id="a3025-155">**ELEMENT_TYPE_SZARRAY\*\*\*\*\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="a3025-155">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="a3025-156">Rank = 1, dolní mez = 0.</span><span class="sxs-lookup"><span data-stu-id="a3025-156">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="a3025-157">Velikost je známá pouze v případě, že je k dispozici ve spravovaném podpisu.</span><span class="sxs-lookup"><span data-stu-id="a3025-157">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="a3025-158">Bezpečná pole</span><span class="sxs-lookup"><span data-stu-id="a3025-158">Safe Arrays</span></span>  
 <span data-ttu-id="a3025-159">Když je bezpečné pole importováno z knihovny typů do sestavení .NET, pole je převedeno na jednorozměrné pole známého typu (například **int**).</span><span class="sxs-lookup"><span data-stu-id="a3025-159">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="a3025-160">Stejná pravidla převodu typů, která platí pro parametry, platí také pro prvky pole.</span><span class="sxs-lookup"><span data-stu-id="a3025-160">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="a3025-161">Například bezpečné pole typů **BSTR** se stávají spravovaným polem řetězců a bezpečné pole variant se stávají spravovaným polem objektů.</span><span class="sxs-lookup"><span data-stu-id="a3025-161">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="a3025-162">Typ elementu **SAFEARRAY** je zachycen z knihovny typů a uložen v hodnotě **SAFEARRAY** <xref:System.Runtime.InteropServices.UnmanagedType> výčtu.</span><span class="sxs-lookup"><span data-stu-id="a3025-162">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="a3025-163">Vzhledem k tomu, že pořadí a meze bezpečného pole nelze určit z knihovny typů, předpokládá se, že pořadí je rovno 1 a dolní mez je rovna 0.</span><span class="sxs-lookup"><span data-stu-id="a3025-163">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="a3025-164">Pořadí a meze musí být definovány ve spravovaném podpisu vytvořeném modulem pro [Import knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="a3025-164">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="a3025-165">Pokud pořadí předané metodě v době běhu se liší, <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="a3025-165">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="a3025-166">Pokud se typ pole předaného v době běhu liší, <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="a3025-166">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="a3025-167">Následující příklad zobrazuje bezpečná pole ve spravovaném a nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="a3025-167">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="a3025-168">**Nespravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="a3025-168">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="a3025-169">**Spravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="a3025-169">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]
   ref String[] ar);  
```  
  
 <span data-ttu-id="a3025-170">Vícerozměrné nebo nenulové bezpečné pole, lze zařadit do spravovaného kódu, pokud je podpis metody vytvořený pomocí Tlbimp.exe změněn tak, aby označoval typ prvku **ELEMENT_TYPE_ARRAY** namísto **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="a3025-170">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="a3025-171">Alternativně můžete použít přepínač **/sysarray** s Tlbimp.exe pro import všech polí jako <xref:System.Array?displayProperty=nameWithType> objektů.</span><span class="sxs-lookup"><span data-stu-id="a3025-171">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="a3025-172">V případech, kdy je předávané pole známo multidimenzionální, můžete upravit kód jazyka MSIL (Microsoft Intermediate Language) vytvořený pomocí Tlbimp.exe a poté jej znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="a3025-172">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="a3025-173">Podrobnosti o tom, jak upravit kód jazyka MSIL, najdete v tématu [přizpůsobení obálek za běhu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)), které lze volat.</span><span class="sxs-lookup"><span data-stu-id="a3025-173">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="a3025-174">Pole stylu C</span><span class="sxs-lookup"><span data-stu-id="a3025-174">C-Style Arrays</span></span>  
 <span data-ttu-id="a3025-175">Když je pole ve stylu jazyka C importováno z knihovny typů do sestavení .NET, pole je převedeno na **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="a3025-175">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="a3025-176">Typ prvku pole je určen z knihovny typů a zůstane během importu.</span><span class="sxs-lookup"><span data-stu-id="a3025-176">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="a3025-177">Stejná pravidla převodu, která platí pro parametry, platí také pro prvky pole.</span><span class="sxs-lookup"><span data-stu-id="a3025-177">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="a3025-178">Například pole typů **typem LPStr** se stávají polem typů **řetězců** .</span><span class="sxs-lookup"><span data-stu-id="a3025-178">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="a3025-179">Tlbimp.exe zachycuje typ prvku pole a aplikuje <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut na parametr.</span><span class="sxs-lookup"><span data-stu-id="a3025-179">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="a3025-180">Předpokládá se, že se rozměr pole rovná 1.</span><span class="sxs-lookup"><span data-stu-id="a3025-180">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="a3025-181">Pokud je pořadí větší než 1, pole je zařazeno jako jednorozměrné pole v pořadí podle sloupců.</span><span class="sxs-lookup"><span data-stu-id="a3025-181">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="a3025-182">Dolní mez se vždycky rovná 0.</span><span class="sxs-lookup"><span data-stu-id="a3025-182">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="a3025-183">Knihovny typů mohou obsahovat pole s pevnou nebo proměnlivou délkou.</span><span class="sxs-lookup"><span data-stu-id="a3025-183">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="a3025-184">Tlbimp.exe mohou importovat pouze pole s pevnou délkou z knihoven typů, protože knihovny typů nemají informace potřebné pro zařazování polí s proměnnou délkou.</span><span class="sxs-lookup"><span data-stu-id="a3025-184">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="a3025-185">S poli s pevnou délkou je velikost importována z knihovny typů a zachycena v **MarshalAsAttribute** , která je použita pro parametr.</span><span class="sxs-lookup"><span data-stu-id="a3025-185">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="a3025-186">Je nutné ručně definovat knihovny typů obsahující pole s proměnnou délkou, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a3025-186">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="a3025-187">**Nespravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="a3025-187">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="a3025-188">**Spravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="a3025-188">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 <span data-ttu-id="a3025-189">I když můžete použít atributy **size_is** nebo **length_is** na pole ve zdroji rozhraní IDL (Interface Definition Language) pro předávání velikosti klientovi, kompilátor rozhraní Microsoft Interface Definition Language (MIDL) tyto informace nerozšíří do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="a3025-189">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="a3025-190">Bez znalosti velikosti nemůže služba interop marshaling zařadit prvky pole.</span><span class="sxs-lookup"><span data-stu-id="a3025-190">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="a3025-191">V důsledku toho se pole s proměnlivou délkou importují jako argumenty reference.</span><span class="sxs-lookup"><span data-stu-id="a3025-191">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="a3025-192">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a3025-192">For example:</span></span>  
  
 <span data-ttu-id="a3025-193">**Nespravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="a3025-193">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="a3025-194">**Spravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="a3025-194">**Managed signature**</span></span>  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
```  
  
```csharp  
void New1(ref int ar);
void New2(ref double ar);
void New3(ref String ar);
```  
  
 <span data-ttu-id="a3025-195">Zařazovacímu programu můžete poskytnout velikost pole úpravou kódu jazyka MSIL (Microsoft Intermediate Language) vytvořeného pomocí Tlbimp.exe a opětovnou kompilací.</span><span class="sxs-lookup"><span data-stu-id="a3025-195">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="a3025-196">Podrobnosti o tom, jak upravit kód jazyka MSIL, najdete v tématu [přizpůsobení obálek za běhu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)), které lze volat.</span><span class="sxs-lookup"><span data-stu-id="a3025-196">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="a3025-197">Chcete-li určit počet prvků v poli, použijte <xref:System.Runtime.InteropServices.MarshalAsAttribute> typ pro parametr pole definice spravované metody jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="a3025-197">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
- <span data-ttu-id="a3025-198">Identifikujte další parametr, který obsahuje počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="a3025-198">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="a3025-199">Parametry jsou identifikovány podle pozice počínaje prvním parametrem jako číslo 0.</span><span class="sxs-lookup"><span data-stu-id="a3025-199">The parameters are identified by position, starting with the first parameter as number 0.</span></span>
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       \<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
- <span data-ttu-id="a3025-200">Definujte velikost pole jako konstantu.</span><span class="sxs-lookup"><span data-stu-id="a3025-200">Define the size of the array as a constant.</span></span> <span data-ttu-id="a3025-201">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a3025-201">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="a3025-202">Při zařazování polí z nespravovaného kódu do spravovaného kódu zařazovací modul zkontroluje **MarshalAsAttribute** přidružený k parametru a určí velikost pole.</span><span class="sxs-lookup"><span data-stu-id="a3025-202">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="a3025-203">Pokud není určena velikost pole, je zařazen pouze jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="a3025-203">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3025-204">**MarshalAsAttribute** nemá žádný vliv na zařazování spravovaných polí do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="a3025-204">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="a3025-205">V tomto směru je velikost pole určena kontrolou.</span><span class="sxs-lookup"><span data-stu-id="a3025-205">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="a3025-206">Neexistuje žádný způsob, jak zařadit podmnožinu spravovaného pole.</span><span class="sxs-lookup"><span data-stu-id="a3025-206">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="a3025-207">Zařazovací modul Interop používá metody **CoTaskMemAlloc** a **CoTaskMemFree** k přidělení a načtení paměti.</span><span class="sxs-lookup"><span data-stu-id="a3025-207">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="a3025-208">Tyto metody musí používat i přidělení paměti prováděné nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="a3025-208">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
## <a name="passing-arrays-to-com"></a><span data-ttu-id="a3025-209">Předávání polí do modelu COM</span><span class="sxs-lookup"><span data-stu-id="a3025-209">Passing Arrays to COM</span></span>  
 <span data-ttu-id="a3025-210">Všechny typy spravovaných polí lze předat nespravovanému kódu ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="a3025-210">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="a3025-211">V závislosti na spravovaném typu a použitých atributech může být pole dostupné jako bezpečné pole nebo ve stylu jazyka C, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a3025-211">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="a3025-212">Typ spravovaného pole</span><span class="sxs-lookup"><span data-stu-id="a3025-212">Managed array type</span></span>|<span data-ttu-id="a3025-213">Exportováno jako</span><span class="sxs-lookup"><span data-stu-id="a3025-213">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="a3025-214">**ELEMENT_TYPE_SZARRAY\*\*\*\*\<** *type* **>**</span><span class="sxs-lookup"><span data-stu-id="a3025-214">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="a3025-215"><xref:System.Runtime.InteropServices.UnmanagedType>**. SafeArray (** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="a3025-215"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="a3025-216">**UnmanagedType. typy LPArray**</span><span class="sxs-lookup"><span data-stu-id="a3025-216">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="a3025-217">V signatuře je uveden typ.</span><span class="sxs-lookup"><span data-stu-id="a3025-217">Type is provided in the signature.</span></span> <span data-ttu-id="a3025-218">Pořadí je vždy 1, dolní hranice je vždy 0.</span><span class="sxs-lookup"><span data-stu-id="a3025-218">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="a3025-219">Velikost je vždy známá v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a3025-219">Size is always known at run time.</span></span>|  
|<span data-ttu-id="a3025-220">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span><span class="sxs-lookup"><span data-stu-id="a3025-220">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="a3025-221">**UnmanagedType. SAFEARRAY (** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="a3025-221">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="a3025-222">**UnmanagedType. typy LPArray**</span><span class="sxs-lookup"><span data-stu-id="a3025-222">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="a3025-223">Typ, rozsah, meze jsou k dispozici v signatuře.</span><span class="sxs-lookup"><span data-stu-id="a3025-223">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="a3025-224">Velikost je vždy známá v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a3025-224">Size is always known at run time.</span></span>|  
|<span data-ttu-id="a3025-225">**ELEMENT_TYPE_CLASS\*\*\*\*\<**<xref:System.Array?displayProperty=nameWithType>**>\*\*</span><span class="sxs-lookup"><span data-stu-id="a3025-225">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>\*\*</span></span>|<span data-ttu-id="a3025-226">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="a3025-226">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="a3025-227">**UnmanagedType. SAFEARRAY (** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="a3025-227">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="a3025-228">Typ, pořadí, meze a velikost jsou vždy známy v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a3025-228">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="a3025-229">V automatizaci OLE existuje omezení související s poli struktur, která obsahují typem LPStr nebo LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="a3025-229">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="a3025-230">Proto musí být pole **řetězců** zařazena jako **UnmanagedType. BSTR**.</span><span class="sxs-lookup"><span data-stu-id="a3025-230">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="a3025-231">V opačném případě bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="a3025-231">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="element_type_szarray"></a><span data-ttu-id="a3025-232">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="a3025-232">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="a3025-233">Pokud je metoda obsahující **ELEMENT_TYPE_SZARRAY** parametr (jednorozměrné pole) exportována ze sestavení .NET do knihovny typů, je parametr pole převeden na hodnotu **SAFEARRAY** daného typu.</span><span class="sxs-lookup"><span data-stu-id="a3025-233">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="a3025-234">Stejná pravidla převodu se vztahují na typy prvků pole.</span><span class="sxs-lookup"><span data-stu-id="a3025-234">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="a3025-235">Obsah spravovaného pole se automaticky zkopíruje ze spravované paměti do pole **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="a3025-235">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="a3025-236">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a3025-236">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="a3025-237">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="a3025-237">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="a3025-238">Nespravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="a3025-238">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="a3025-239">Rozsah bezpečných polí je vždycky 1 a dolní hranice je vždycky 0.</span><span class="sxs-lookup"><span data-stu-id="a3025-239">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="a3025-240">Velikost je určena v době běhu podle velikosti předávaného spravovaného pole.</span><span class="sxs-lookup"><span data-stu-id="a3025-240">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="a3025-241">Pole lze také zařadit jako pole ve stylu jazyka C pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="a3025-241">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="a3025-242">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a3025-242">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="a3025-243">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="a3025-243">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=
   UnmanagedType.LPStr, SizeParamIndex=1)]
   String [] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="a3025-244">Nespravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="a3025-244">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="a3025-245">I když zařazovací jednotka má informace o délce potřebné k zařazení pole, délka pole je obvykle předána jako samostatný argument pro vyjádření délky volaného.</span><span class="sxs-lookup"><span data-stu-id="a3025-245">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="element_type_array"></a><span data-ttu-id="a3025-246">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="a3025-246">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="a3025-247">Pokud je metoda obsahující **ELEMENT_TYPE_ARRAY** parametr exportována ze sestavení .NET do knihovny typů, je parametr pole převeden na hodnotu **SAFEARRAY** daného typu.</span><span class="sxs-lookup"><span data-stu-id="a3025-247">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="a3025-248">Obsah spravovaného pole se automaticky zkopíruje ze spravované paměti do pole **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="a3025-248">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="a3025-249">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a3025-249">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="a3025-250">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="a3025-250">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="a3025-251">Nespravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="a3025-251">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="a3025-252">Pořadí, velikost a hranice bezpečných polí jsou určeny za běhu podle vlastností spravovaného pole.</span><span class="sxs-lookup"><span data-stu-id="a3025-252">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="a3025-253">Pole lze také zařadit jako pole ve stylu jazyka C použitím <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="a3025-253">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="a3025-254">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a3025-254">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="a3025-255">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="a3025-255">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]
   String [,] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="a3025-256">Nespravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="a3025-256">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="a3025-257">Vnořená pole nelze zařadit.</span><span class="sxs-lookup"><span data-stu-id="a3025-257">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="a3025-258">Například následující signatura generuje chybu při exportu pomocí [typu Exportér knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="a3025-258">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="a3025-259">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="a3025-259">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a><span data-ttu-id="a3025-260">ELEMENT_TYPE_CLASS\<System.Array></span><span class="sxs-lookup"><span data-stu-id="a3025-260">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="a3025-261">Je-li metoda, která obsahuje <xref:System.Array?displayProperty=nameWithType> parametr, exportována ze sestavení .NET do knihovny typů, je parametr pole převeden na **_array** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a3025-261">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="a3025-262">Obsah spravovaného pole je přístupný pouze prostřednictvím metod a vlastností rozhraní **_array** .</span><span class="sxs-lookup"><span data-stu-id="a3025-262">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="a3025-263">**System. Array** se dá také zařadit jako **SAFEARRAY** pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="a3025-263">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="a3025-264">Při zařazování jako bezpečné pole jsou prvky pole zařazeny jako varianty.</span><span class="sxs-lookup"><span data-stu-id="a3025-264">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="a3025-265">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a3025-265">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="a3025-266">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="a3025-266">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="a3025-267">Nespravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="a3025-267">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="a3025-268">Pole ve strukturách</span><span class="sxs-lookup"><span data-stu-id="a3025-268">Arrays within Structures</span></span>  
 <span data-ttu-id="a3025-269">Nespravované struktury mohou obsahovat vložená pole.</span><span class="sxs-lookup"><span data-stu-id="a3025-269">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="a3025-270">Ve výchozím nastavení jsou tato vložená pole pole zařazena jako SAFEARRAY.</span><span class="sxs-lookup"><span data-stu-id="a3025-270">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="a3025-271">V následujícím příkladu `s1` je vloženo pole, které je přiděleno přímo v rámci struktury samotné.</span><span class="sxs-lookup"><span data-stu-id="a3025-271">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="a3025-272">Nespravované reprezentace</span><span class="sxs-lookup"><span data-stu-id="a3025-272">Unmanaged representation</span></span>  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="a3025-273">Pole lze zařadit jako <xref:System.Runtime.InteropServices.UnmanagedType> , což vyžaduje, abyste nastavili <xref:System.Runtime.InteropServices.MarshalAsAttribute> pole.</span><span class="sxs-lookup"><span data-stu-id="a3025-273">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="a3025-274">Velikost lze nastavit pouze jako konstantu.</span><span class="sxs-lookup"><span data-stu-id="a3025-274">The size can be set only as a constant.</span></span> <span data-ttu-id="a3025-275">Následující kód ukazuje odpovídající spravovanou definici `MyStruct` .</span><span class="sxs-lookup"><span data-stu-id="a3025-275">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3025-276">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3025-276">See also</span></span>

- [<span data-ttu-id="a3025-277">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="a3025-277">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="a3025-278">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="a3025-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="a3025-279">[Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a3025-279">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="a3025-280">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="a3025-280">Copying and Pinning</span></span>](copying-and-pinning.md)
