---
title: Výchozí zařazování pro pole
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
ms.openlocfilehash: f0094ac572834b2cf0d74fb53c94877da55669e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181447"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="25d1a-102">Výchozí zařazování pro pole</span><span class="sxs-lookup"><span data-stu-id="25d1a-102">Default Marshaling for Arrays</span></span>
<span data-ttu-id="25d1a-103">V aplikaci, která se skládá výhradně ze spravovaného kódu, předává soubor typu common jazyka typem pole jako parametry In/Out.</span><span class="sxs-lookup"><span data-stu-id="25d1a-103">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="25d1a-104">Naproti tomu interop zařazovací zařízení ve výchozím nastavení předá pole jako parametry In.</span><span class="sxs-lookup"><span data-stu-id="25d1a-104">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="25d1a-105">S [připnutí optimalizace](copying-and-pinning.md), přenositelné pole se může jevit jako in/out parametr při interakci s objekty ve stejném apartment.</span><span class="sxs-lookup"><span data-stu-id="25d1a-105">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="25d1a-106">Pokud však později exportujete kód do knihovny typů, která slouží ke generování proxy serveru mezi počítači, a tato knihovna se používá k zařazování volání mezi byty, volání se mohou vrátit k chování parametrů true In.</span><span class="sxs-lookup"><span data-stu-id="25d1a-106">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="25d1a-107">Pole jsou komplexní povahy a rozdíly mezi spravovanými a nespravovanými poli vyžadují více informací než jiné typy, které nejsou přenositelné.</span><span class="sxs-lookup"><span data-stu-id="25d1a-107">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span>  
  
## <a name="managed-arrays"></a><span data-ttu-id="25d1a-108">Spravovaná pole</span><span class="sxs-lookup"><span data-stu-id="25d1a-108">Managed Arrays</span></span>  
 <span data-ttu-id="25d1a-109">Typy spravovaných polí se mohou lišit. <xref:System.Array?displayProperty=nameWithType> třída je však základní třídou všech typů polí.</span><span class="sxs-lookup"><span data-stu-id="25d1a-109">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="25d1a-110">Třída **System.Array** má vlastnosti pro určení pořadí, délky a dolnía horní hranice pole, stejně jako metody pro přístup, řazení, vyhledávání, kopírování a vytváření polí.</span><span class="sxs-lookup"><span data-stu-id="25d1a-110">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="25d1a-111">Tyto typy polí jsou dynamické a nemají odpovídající statický typ definovaný v knihovně základní třídy.</span><span class="sxs-lookup"><span data-stu-id="25d1a-111">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="25d1a-112">Je vhodné si myslet, že každá kombinace typu prvku a pořadí jako odlišný typ pole.</span><span class="sxs-lookup"><span data-stu-id="25d1a-112">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="25d1a-113">Proto jednorozměrné pole celá čísla je jiného typu než jednorozměrné pole dvojité typy.</span><span class="sxs-lookup"><span data-stu-id="25d1a-113">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="25d1a-114">Podobně dvojrozměrné pole celá čísla se liší od jednorozměrné pole celá čísla.</span><span class="sxs-lookup"><span data-stu-id="25d1a-114">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="25d1a-115">Hranice pole nejsou považovány za při porovnávání typů.</span><span class="sxs-lookup"><span data-stu-id="25d1a-115">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="25d1a-116">Jak ukazuje následující tabulka, každá instance spravovaného pole musí mít určitý typ prvku, pořadí a dolní mez.</span><span class="sxs-lookup"><span data-stu-id="25d1a-116">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="25d1a-117">Typ spravovaného pole</span><span class="sxs-lookup"><span data-stu-id="25d1a-117">Managed array type</span></span>|<span data-ttu-id="25d1a-118">Typ prvku</span><span class="sxs-lookup"><span data-stu-id="25d1a-118">Element type</span></span>|<span data-ttu-id="25d1a-119">Rank</span><span class="sxs-lookup"><span data-stu-id="25d1a-119">Rank</span></span>|<span data-ttu-id="25d1a-120">Dolní mez</span><span class="sxs-lookup"><span data-stu-id="25d1a-120">Lower bound</span></span>|<span data-ttu-id="25d1a-121">Zápis podpisu</span><span class="sxs-lookup"><span data-stu-id="25d1a-121">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="25d1a-122">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="25d1a-122">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="25d1a-123">Zadaný podle typu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-123">Specified by type.</span></span>|<span data-ttu-id="25d1a-124">Určeno pořadím.</span><span class="sxs-lookup"><span data-stu-id="25d1a-124">Specified by rank.</span></span>|<span data-ttu-id="25d1a-125">Volitelně zadaná hranicemi.</span><span class="sxs-lookup"><span data-stu-id="25d1a-125">Optionally specified by bounds.</span></span>|<span data-ttu-id="25d1a-126">*typ* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="25d1a-126">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="25d1a-127">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="25d1a-127">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="25d1a-128">Není známo</span><span class="sxs-lookup"><span data-stu-id="25d1a-128">Unknown</span></span>|<span data-ttu-id="25d1a-129">Není známo</span><span class="sxs-lookup"><span data-stu-id="25d1a-129">Unknown</span></span>|<span data-ttu-id="25d1a-130">Není známo</span><span class="sxs-lookup"><span data-stu-id="25d1a-130">Unknown</span></span>|<span data-ttu-id="25d1a-131">**System.array**</span><span class="sxs-lookup"><span data-stu-id="25d1a-131">**System.Array**</span></span>|  
|<span data-ttu-id="25d1a-132">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="25d1a-132">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="25d1a-133">Zadaný podle typu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-133">Specified by type.</span></span>|<span data-ttu-id="25d1a-134">1</span><span class="sxs-lookup"><span data-stu-id="25d1a-134">1</span></span>|<span data-ttu-id="25d1a-135">0</span><span class="sxs-lookup"><span data-stu-id="25d1a-135">0</span></span>|<span data-ttu-id="25d1a-136">*typ* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="25d1a-136">*type* **[** *n* **]**</span></span>|  
  
## <a name="unmanaged-arrays"></a><span data-ttu-id="25d1a-137">Nespravovaná pole</span><span class="sxs-lookup"><span data-stu-id="25d1a-137">Unmanaged Arrays</span></span>  
 <span data-ttu-id="25d1a-138">Nespravovaná pole jsou buď bezpečná pole ve stylu COM, nebo pole ve stylu C s pevnou nebo proměnnou délkou.</span><span class="sxs-lookup"><span data-stu-id="25d1a-138">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="25d1a-139">Bezpečná pole jsou pole popisující sám sebe, která nesou typ, pořadí a hranice přidružených dat pole.</span><span class="sxs-lookup"><span data-stu-id="25d1a-139">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="25d1a-140">Pole ve stylu C jsou jednorozměrná pole s pevnou dolní mezí 0.</span><span class="sxs-lookup"><span data-stu-id="25d1a-140">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="25d1a-141">Zařazovací služba má omezenou podporu pro oba typy polí.</span><span class="sxs-lookup"><span data-stu-id="25d1a-141">The marshaling service has limited support for both types of arrays.</span></span>  
  
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="25d1a-142">Předání parametrů pole kódu .NET</span><span class="sxs-lookup"><span data-stu-id="25d1a-142">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="25d1a-143">Pole ve stylu C i bezpečná pole mohou být předána kódu .NET z nespravovaného kódu jako bezpečné pole nebo pole ve stylu C.</span><span class="sxs-lookup"><span data-stu-id="25d1a-143">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="25d1a-144">V následující tabulce je uvedena hodnota nespravovaného typu a importovaný typ.</span><span class="sxs-lookup"><span data-stu-id="25d1a-144">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="25d1a-145">Nespravovaný typ</span><span class="sxs-lookup"><span data-stu-id="25d1a-145">Unmanaged type</span></span>|<span data-ttu-id="25d1a-146">Importovaný typ</span><span class="sxs-lookup"><span data-stu-id="25d1a-146">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="25d1a-147">**SafeArray(** *Typ* **)**</span><span class="sxs-lookup"><span data-stu-id="25d1a-147">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="25d1a-148">**ELEMENT_TYPE_SZARRAY** **\<** *převedený typ\*\*\*>*\*</span><span class="sxs-lookup"><span data-stu-id="25d1a-148">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="25d1a-149">Pořadí = 1, dolní mez = 0.</span><span class="sxs-lookup"><span data-stu-id="25d1a-149">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="25d1a-150">Velikost je známa pouze v případě, že je k dispozici ve spravovaném podpisu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-150">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="25d1a-151">Bezpečná pole, která nejsou kategorie = 1 nebo dolní mez = 0 nelze zařadit jako **SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="25d1a-151">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="25d1a-152">*Typ*  **[]**</span><span class="sxs-lookup"><span data-stu-id="25d1a-152">*Type*  **[]**</span></span>|<span data-ttu-id="25d1a-153">**ELEMENT_TYPE_SZARRAY** **\<** *převedený typ\*\*\*>*\*</span><span class="sxs-lookup"><span data-stu-id="25d1a-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="25d1a-154">Pořadí = 1, dolní mez = 0.</span><span class="sxs-lookup"><span data-stu-id="25d1a-154">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="25d1a-155">Velikost je známa pouze v případě, že je k dispozici ve spravovaném podpisu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-155">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="25d1a-156">Bezpečná pole</span><span class="sxs-lookup"><span data-stu-id="25d1a-156">Safe Arrays</span></span>  
 <span data-ttu-id="25d1a-157">Při importu bezpečného pole z knihovny typů do sestavení .NET je pole převedeno na jednorozměrné pole známého typu (například **int).**</span><span class="sxs-lookup"><span data-stu-id="25d1a-157">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="25d1a-158">Stejná pravidla převodu typu, která platí pro parametry, platí také pro prvky pole.</span><span class="sxs-lookup"><span data-stu-id="25d1a-158">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="25d1a-159">Například bezpečné pole **bstr** typů se stane spravované pole řetězců a bezpečné pole variant se stane spravované pole objektů.</span><span class="sxs-lookup"><span data-stu-id="25d1a-159">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="25d1a-160">Typ prvku **SAFEARRAY** je zachycen z knihovny typů a uložen <xref:System.Runtime.InteropServices.UnmanagedType> v hodnotě **SAFEARRAY** výčtu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-160">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="25d1a-161">Vzhledem k tomu, že pořadí a hranice bezpečného pole nelze určit z knihovny typů, předpokládá se, že pořadí se rovná 1 a dolní mez se rovná 0.</span><span class="sxs-lookup"><span data-stu-id="25d1a-161">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="25d1a-162">Pořadí a hranice musí být definovány ve spravovaném podpisu vytvořeném [typem knihovny Dovozce (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="25d1a-162">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="25d1a-163">Pokud pořadí předán metodě v době běhu <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> se liší, je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="25d1a-163">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="25d1a-164">Pokud se typ pole předaný za <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> běhu liší, je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="25d1a-164">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="25d1a-165">Následující příklad ukazuje bezpečná pole ve spravovaném a nespravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-165">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="25d1a-166">**Nespravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="25d1a-166">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="25d1a-167">**Spravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="25d1a-167">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="25d1a-168">Multidimenzionální nebo nenulová bezpečná pole mohou být zařazena do spravovaného kódu, pokud je podpis metody vytvořený programem Tlbimp.exe upraven tak, aby označoval typ prvku **ELEMENT_TYPE_ARRAY** namísto **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="25d1a-168">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="25d1a-169">Alternativně můžete použít přepínač **/sysarray** s tlbimp.exe k <xref:System.Array?displayProperty=nameWithType> importu všech polí jako objektů.</span><span class="sxs-lookup"><span data-stu-id="25d1a-169">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="25d1a-170">V případech, kdy je předané pole známo, že je vícerozměrné, můžete upravit kód zprostředkující jazyk společnosti Microsoft (MSIL) vytvořený souborem Tlbimp.exe a poté jej znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="25d1a-170">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="25d1a-171">Podrobnosti o úpravě kódu MSIL naleznete [v tématu Přizpůsobení reložiových obkladů volání runtime](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="25d1a-171">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="25d1a-172">Pole ve stylu C</span><span class="sxs-lookup"><span data-stu-id="25d1a-172">C-Style Arrays</span></span>  
 <span data-ttu-id="25d1a-173">Při importu pole ve stylu C z knihovny typů do sestavení .NET je pole převedeno na **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="25d1a-173">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="25d1a-174">Typ prvku pole je určen z knihovny typů a během importu se zachová.</span><span class="sxs-lookup"><span data-stu-id="25d1a-174">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="25d1a-175">Stejná pravidla převodu, která platí pro parametry, platí také pro prvky pole.</span><span class="sxs-lookup"><span data-stu-id="25d1a-175">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="25d1a-176">Například pole **LPStr** typy se stane pole **String** typy.</span><span class="sxs-lookup"><span data-stu-id="25d1a-176">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="25d1a-177">Tlbimp.exe zachycuje typ prvku pole a <xref:System.Runtime.InteropServices.MarshalAsAttribute> aplikuje atribut na parametr.</span><span class="sxs-lookup"><span data-stu-id="25d1a-177">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="25d1a-178">Pořadí pole se předpokládá, že se rovná 1.</span><span class="sxs-lookup"><span data-stu-id="25d1a-178">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="25d1a-179">Pokud je pořadí větší než 1, pole je zařazeno jako jednorozměrné pole v pořadí sloupce hlavní.</span><span class="sxs-lookup"><span data-stu-id="25d1a-179">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="25d1a-180">Dolní mez se vždy rovná 0.</span><span class="sxs-lookup"><span data-stu-id="25d1a-180">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="25d1a-181">Knihovny typů mohou obsahovat pole s pevnou nebo proměnnou délkou.</span><span class="sxs-lookup"><span data-stu-id="25d1a-181">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="25d1a-182">Tlbimp.exe lze importovat pouze pole s pevnou délkou z knihoven typů, protože knihovny typů postrádají informace potřebné k zařazování polí s proměnnou délkou.</span><span class="sxs-lookup"><span data-stu-id="25d1a-182">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="25d1a-183">U polí s pevnou délkou je velikost importována z knihovny typů a zachycena v **atributu MarshalAsAttribute,** který je použit pro parametr.</span><span class="sxs-lookup"><span data-stu-id="25d1a-183">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="25d1a-184">Je nutné ručně definovat knihovny typů obsahující pole proměnné délky, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-184">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="25d1a-185">**Nespravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="25d1a-185">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="25d1a-186">**Spravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="25d1a-186">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="25d1a-187">Přestože můžete použít **atributy size_is** nebo **length_is** na pole ve zdroji IDL (Interface Definition Language) pro přenos velikosti klientovi, kompilátor jazyka MIDL (Microsoft Interface Definition Language) tyto informace do knihovny typů nerozšíří.</span><span class="sxs-lookup"><span data-stu-id="25d1a-187">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="25d1a-188">Bez znalosti velikosti nemůže zařazovací služba interop zařazovat prvky pole.</span><span class="sxs-lookup"><span data-stu-id="25d1a-188">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="25d1a-189">V důsledku toho jsou pole proměnné délky importována jako referenční argumenty.</span><span class="sxs-lookup"><span data-stu-id="25d1a-189">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="25d1a-190">Například:</span><span class="sxs-lookup"><span data-stu-id="25d1a-190">For example:</span></span>  
  
 <span data-ttu-id="25d1a-191">**Nespravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="25d1a-191">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="25d1a-192">**Spravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="25d1a-192">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="25d1a-193">Zařazování můžete poskytnout velikost pole úpravou kódu MSIL (MSIL) společnosti Microsoft vytvořeného souborem Tlbimp.exe a jeho opětovnou kompilací.</span><span class="sxs-lookup"><span data-stu-id="25d1a-193">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="25d1a-194">Podrobnosti o úpravě kódu MSIL naleznete [v tématu Přizpůsobení reložiových obkladů volání runtime](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="25d1a-194">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="25d1a-195">Chcete-li označit počet prvků v <xref:System.Runtime.InteropServices.MarshalAsAttribute> poli, použijte typ na parametr pole definice spravované metody jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="25d1a-195">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
- <span data-ttu-id="25d1a-196">Identifikujte jiný parametr, který obsahuje počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="25d1a-196">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="25d1a-197">Parametry jsou identifikovány podle pozice, počínaje prvním parametrem jako číslo 0.</span><span class="sxs-lookup"><span data-stu-id="25d1a-197">The parameters are identified by position, starting with the first parameter as number 0.</span></span>
  
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
  
- <span data-ttu-id="25d1a-198">Definujte velikost pole jako konstantu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-198">Define the size of the array as a constant.</span></span> <span data-ttu-id="25d1a-199">Například:</span><span class="sxs-lookup"><span data-stu-id="25d1a-199">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="25d1a-200">Při zařazování polí z nespravovaného kódu na spravovaný kód zařazuje **marshalAsAttribute** přidružený k parametru k určení velikosti pole.</span><span class="sxs-lookup"><span data-stu-id="25d1a-200">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="25d1a-201">Pokud není zadána velikost pole, je zařazen pouze jeden prvek.</span><span class="sxs-lookup"><span data-stu-id="25d1a-201">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25d1a-202">**MarshalAsAttribute** nemá žádný vliv na zařazování spravovaných polí do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-202">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="25d1a-203">V tomto směru je velikost pole určena vyšetřením.</span><span class="sxs-lookup"><span data-stu-id="25d1a-203">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="25d1a-204">Neexistuje žádný způsob, jak zařadit podmnožinu spravovaného pole.</span><span class="sxs-lookup"><span data-stu-id="25d1a-204">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="25d1a-205">Interop zařazování používá **CoTaskMemAlloc** a **CoTaskMemFree** metody přidělit a načíst paměť.</span><span class="sxs-lookup"><span data-stu-id="25d1a-205">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="25d1a-206">Přidělení paměti prováděné nespravovaným kódem musí také používat tyto metody.</span><span class="sxs-lookup"><span data-stu-id="25d1a-206">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
## <a name="passing-arrays-to-com"></a><span data-ttu-id="25d1a-207">Předávání polí com</span><span class="sxs-lookup"><span data-stu-id="25d1a-207">Passing Arrays to COM</span></span>  
 <span data-ttu-id="25d1a-208">Všechny typy spravovaných polí lze předat nespravovanému kódu ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-208">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="25d1a-209">V závislosti na spravovaném typu a atributech, které jsou na něj použity, lze k poli přistupovat jako k bezpečnému poli nebo poli ve stylu C, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="25d1a-209">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="25d1a-210">Typ spravovaného pole</span><span class="sxs-lookup"><span data-stu-id="25d1a-210">Managed array type</span></span>|<span data-ttu-id="25d1a-211">Exportováno jako</span><span class="sxs-lookup"><span data-stu-id="25d1a-211">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="25d1a-212">**typ ELEMENT_TYPE_SZARRAY** **\<** *type\*\*\*>*\*</span><span class="sxs-lookup"><span data-stu-id="25d1a-212">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="25d1a-213"><xref:System.Runtime.InteropServices.UnmanagedType>**. SafeArray(** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="25d1a-213"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="25d1a-214">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="25d1a-214">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="25d1a-215">Typ je k dispozici v podpisu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-215">Type is provided in the signature.</span></span> <span data-ttu-id="25d1a-216">Pořadí je vždy 1, dolní mez je vždy 0.</span><span class="sxs-lookup"><span data-stu-id="25d1a-216">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="25d1a-217">Velikost je vždy známa za běhu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-217">Size is always known at run time.</span></span>|  
|<span data-ttu-id="25d1a-218">**ELEMENT_TYPE_ARRAY** **\<** *pořadí* **>** **\<** *rank* **\<** *bounds* **>** typů [ hranice ] **>**</span><span class="sxs-lookup"><span data-stu-id="25d1a-218">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="25d1a-219">**UnmanagedType.SafeArray(** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="25d1a-219">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="25d1a-220">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="25d1a-220">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="25d1a-221">Typ, hodnost, hranice jsou uvedeny v podpisu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-221">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="25d1a-222">Velikost je vždy známa za běhu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-222">Size is always known at run time.</span></span>|  
|<span data-ttu-id="25d1a-223">**ELEMENT_TYPE_CLASS\*\*\*\*\<**<xref:System.Array?displayProperty=nameWithType>**>**</span><span class="sxs-lookup"><span data-stu-id="25d1a-223">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span></span>|<span data-ttu-id="25d1a-224">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="25d1a-224">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="25d1a-225">**UnmanagedType.SafeArray(** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="25d1a-225">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="25d1a-226">Typ, pořadí, hranice a velikost jsou vždy známy za běhu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-226">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="25d1a-227">Existuje omezení v ole automatizace týkající se polí struktur, které obsahují LPSTR nebo LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="25d1a-227">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="25d1a-228">Proto **string** pole musí být zařazeny jako **UnmanagedType.BSTR**.</span><span class="sxs-lookup"><span data-stu-id="25d1a-228">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="25d1a-229">V opačném případě bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="25d1a-229">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="element_type_szarray"></a><span data-ttu-id="25d1a-230">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="25d1a-230">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="25d1a-231">Při exportu metody obsahující **parametr ELEMENT_TYPE_SZARRAY** (jednorozměrné pole) ze sestavení .NET do knihovny typů je parametr pole převeden na **SAFEARRAY** daného typu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-231">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="25d1a-232">Stejná pravidla převodu platí pro typy prvků pole.</span><span class="sxs-lookup"><span data-stu-id="25d1a-232">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="25d1a-233">Obsah spravovaného pole se automaticky zkopíruje ze spravované paměti do **safearray**.</span><span class="sxs-lookup"><span data-stu-id="25d1a-233">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="25d1a-234">Například:</span><span class="sxs-lookup"><span data-stu-id="25d1a-234">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="25d1a-235">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="25d1a-235">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="25d1a-236">Nespravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="25d1a-236">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="25d1a-237">Pořadí bezpečných polí je vždy 1 a dolní mez je vždy 0.</span><span class="sxs-lookup"><span data-stu-id="25d1a-237">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="25d1a-238">Velikost je určena v době běhu podle velikosti předávaného spravovaného pole.</span><span class="sxs-lookup"><span data-stu-id="25d1a-238">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="25d1a-239">Pole lze také zařadit jako pole stylu <xref:System.Runtime.InteropServices.MarshalAsAttribute> C pomocí atributu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-239">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="25d1a-240">Například:</span><span class="sxs-lookup"><span data-stu-id="25d1a-240">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="25d1a-241">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="25d1a-241">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="25d1a-242">Nespravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="25d1a-242">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="25d1a-243">Přestože zařazovací zařízení má informace o délce potřebné k zařazovací pole, délka pole je obvykle předána jako samostatný argument pro předávání délky volaného.</span><span class="sxs-lookup"><span data-stu-id="25d1a-243">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="element_type_array"></a><span data-ttu-id="25d1a-244">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="25d1a-244">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="25d1a-245">Při exportu metody obsahující **parametr ELEMENT_TYPE_ARRAY** z sestavení .NET do knihovny typů je parametr pole převeden na **SAFEARRAY** daného typu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-245">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="25d1a-246">Obsah spravovaného pole se automaticky zkopíruje ze spravované paměti do **safearray**.</span><span class="sxs-lookup"><span data-stu-id="25d1a-246">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="25d1a-247">Například:</span><span class="sxs-lookup"><span data-stu-id="25d1a-247">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="25d1a-248">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="25d1a-248">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="25d1a-249">Nespravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="25d1a-249">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="25d1a-250">Pořadí, velikost a hranice bezpečných polí jsou určeny za běhu charakteristikami spravovaného pole.</span><span class="sxs-lookup"><span data-stu-id="25d1a-250">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="25d1a-251">Pole lze také zařadit jako pole stylu <xref:System.Runtime.InteropServices.MarshalAsAttribute> C použitím atributu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-251">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="25d1a-252">Například:</span><span class="sxs-lookup"><span data-stu-id="25d1a-252">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="25d1a-253">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="25d1a-253">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="25d1a-254">Nespravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="25d1a-254">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="25d1a-255">Vnořená pole nelze zařadit.</span><span class="sxs-lookup"><span data-stu-id="25d1a-255">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="25d1a-256">Například následující podpis generuje chybu při exportu s [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="25d1a-256">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="25d1a-257">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="25d1a-257">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a><span data-ttu-id="25d1a-258">> \<ELEMENT_TYPE_CLASS System.Array</span><span class="sxs-lookup"><span data-stu-id="25d1a-258">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="25d1a-259">Při exportu metody <xref:System.Array?displayProperty=nameWithType> obsahující parametr ze sestavení .NET do knihovny typů je parametr pole převeden na **_Array** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="25d1a-259">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="25d1a-260">Obsah spravovaného pole jsou přístupné pouze prostřednictvím metod a vlastností **rozhraní _Array.**</span><span class="sxs-lookup"><span data-stu-id="25d1a-260">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="25d1a-261">**System.Array** lze také zařadit jako **SAFEARRAY** pomocí atributu. <xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="25d1a-261">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="25d1a-262">Při zařazené jako bezpečné pole, prvky pole jsou zařazeny jako varianty.</span><span class="sxs-lookup"><span data-stu-id="25d1a-262">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="25d1a-263">Například:</span><span class="sxs-lookup"><span data-stu-id="25d1a-263">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="25d1a-264">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="25d1a-264">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="25d1a-265">Nespravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="25d1a-265">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="25d1a-266">Pole v rámci struktur</span><span class="sxs-lookup"><span data-stu-id="25d1a-266">Arrays within Structures</span></span>  
 <span data-ttu-id="25d1a-267">Nespravované struktury mohou obsahovat vložená pole.</span><span class="sxs-lookup"><span data-stu-id="25d1a-267">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="25d1a-268">Ve výchozím nastavení jsou tato vložená pole polí zařazena jako SAFEARRAY.</span><span class="sxs-lookup"><span data-stu-id="25d1a-268">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="25d1a-269">V následujícím příkladu je vložené pole, `s1` které je přiděleno přímo v rámci samotné struktury.</span><span class="sxs-lookup"><span data-stu-id="25d1a-269">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="25d1a-270">Nespravovaná reprezentace</span><span class="sxs-lookup"><span data-stu-id="25d1a-270">Unmanaged representation</span></span>  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="25d1a-271">Pole mohou být zařazena jako <xref:System.Runtime.InteropServices.UnmanagedType>, což <xref:System.Runtime.InteropServices.MarshalAsAttribute> vyžaduje nastavení pole.</span><span class="sxs-lookup"><span data-stu-id="25d1a-271">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="25d1a-272">Velikost lze nastavit pouze jako konstantu.</span><span class="sxs-lookup"><span data-stu-id="25d1a-272">The size can be set only as a constant.</span></span> <span data-ttu-id="25d1a-273">Následující kód ukazuje odpovídající spravovanou definici . `MyStruct`</span><span class="sxs-lookup"><span data-stu-id="25d1a-273">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="25d1a-274">Viz také</span><span class="sxs-lookup"><span data-stu-id="25d1a-274">See also</span></span>

- [<span data-ttu-id="25d1a-275">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="25d1a-275">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="25d1a-276">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="25d1a-276">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="25d1a-277">[Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="25d1a-277">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="25d1a-278">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="25d1a-278">Copying and Pinning</span></span>](copying-and-pinning.md)
