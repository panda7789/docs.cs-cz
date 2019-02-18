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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae339b18032becffcaece1924a22b958ed86d364
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219682"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="bdd27-102">Výchozí zařazování pro pole</span><span class="sxs-lookup"><span data-stu-id="bdd27-102">Default Marshaling for Arrays</span></span>
<span data-ttu-id="bdd27-103">V případě aplikace tvořené zcela spravovaný kód modul common language runtime předá typy polí jako vstup a výstup parametry.</span><span class="sxs-lookup"><span data-stu-id="bdd27-103">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="bdd27-104">Naproti tomu interoperační zařazovač předá pole jako parametry in ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="bdd27-104">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="bdd27-105">S [Připnutí optimalizace](copying-and-pinning.md), pole typu blittable můžou zdánlivě pracovat jako vstupně -výstupní parametr při práci s objekty ve stejném objektu apartment.</span><span class="sxs-lookup"><span data-stu-id="bdd27-105">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="bdd27-106">Ale pokud později exportovat do knihovny typů sloužící ke generování mezi počítači proxy kód a tuto knihovnu je použitý k zařazování volání napříč objekty apartment, volání můžete vrátit na hodnotu true parametru chování.</span><span class="sxs-lookup"><span data-stu-id="bdd27-106">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="bdd27-107">Pole jsou komplexní podle povahy a rozdíly mezi spravovanými a nespravovanými pole vyžadují více informace než jiné nepřenositelné typy.</span><span class="sxs-lookup"><span data-stu-id="bdd27-107">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span> <span data-ttu-id="bdd27-108">Toto téma obsahuje následující informace o zařazování polí:</span><span class="sxs-lookup"><span data-stu-id="bdd27-108">This topic provides the following information on marshaling arrays:</span></span>  
  
-   [<span data-ttu-id="bdd27-109">Spravovaná pole</span><span class="sxs-lookup"><span data-stu-id="bdd27-109">Managed Arrays</span></span>](#cpcondefaultmarshalingforarraysanchor1)  
  
-   [<span data-ttu-id="bdd27-110">Nespravované pole</span><span class="sxs-lookup"><span data-stu-id="bdd27-110">Unmanaged Arrays</span></span>](#cpcondefaultmarshalingforarraysanchor2)  
  
-   [<span data-ttu-id="bdd27-111">Předávání parametrů pole pro kód .NET</span><span class="sxs-lookup"><span data-stu-id="bdd27-111">Passing Array Parameters to .NET Code</span></span>](#cpcondefaultmarshalingforarraysanchor3)  
  
-   [<span data-ttu-id="bdd27-112">Předávání polí do modelu COM</span><span class="sxs-lookup"><span data-stu-id="bdd27-112">Passing Arrays to COM</span></span>](#cpcondefaultmarshalingforarraysanchor4)  
  
<a name="cpcondefaultmarshalingforarraysanchor1"></a>   
## <a name="managed-arrays"></a><span data-ttu-id="bdd27-113">Spravovaná pole</span><span class="sxs-lookup"><span data-stu-id="bdd27-113">Managed Arrays</span></span>  
 <span data-ttu-id="bdd27-114">Spravované pole, které mohou být různé typy; ale <xref:System.Array?displayProperty=nameWithType> třída je základní třídou všechny typy polí.</span><span class="sxs-lookup"><span data-stu-id="bdd27-114">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="bdd27-115">**System.Array** třída obsahuje vlastnosti pro určení pořadí, délku a dolní a horní hranice pole, jakož i metody pro přístup k řazení, hledání, kopírování a tvorba polí.</span><span class="sxs-lookup"><span data-stu-id="bdd27-115">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="bdd27-116">Tyto typy polí jsou dynamické vzorce a nemají odpovídající statický typ definovaný v knihovně základních tříd.</span><span class="sxs-lookup"><span data-stu-id="bdd27-116">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="bdd27-117">Je možné mluvit o každou kombinaci typ elementu a řazení jako odlišný typ pole.</span><span class="sxs-lookup"><span data-stu-id="bdd27-117">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="bdd27-118">Jednorozměrné pole celých čísel je proto jiného typu než jednorozměrné pole typu double.</span><span class="sxs-lookup"><span data-stu-id="bdd27-118">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="bdd27-119">Podobně dvourozměrné pole celých čísel se liší od jednorozměrné pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="bdd27-119">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="bdd27-120">Při porovnávání typů, nejsou považovány za hranice pole.</span><span class="sxs-lookup"><span data-stu-id="bdd27-120">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="bdd27-121">V následující tabulce jsou uvedeny, všechny instance spravovaného pole musí být konkrétní elementu typu, pořadí a dolní mez.</span><span class="sxs-lookup"><span data-stu-id="bdd27-121">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="bdd27-122">Spravovaná pole</span><span class="sxs-lookup"><span data-stu-id="bdd27-122">Managed array type</span></span>|<span data-ttu-id="bdd27-123">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="bdd27-123">Element type</span></span>|<span data-ttu-id="bdd27-124">pořadí</span><span class="sxs-lookup"><span data-stu-id="bdd27-124">Rank</span></span>|<span data-ttu-id="bdd27-125">Dolní mez</span><span class="sxs-lookup"><span data-stu-id="bdd27-125">Lower bound</span></span>|<span data-ttu-id="bdd27-126">Zápis podpis</span><span class="sxs-lookup"><span data-stu-id="bdd27-126">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="bdd27-127">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="bdd27-127">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="bdd27-128">Určený typem.</span><span class="sxs-lookup"><span data-stu-id="bdd27-128">Specified by type.</span></span>|<span data-ttu-id="bdd27-129">Určené pořadí.</span><span class="sxs-lookup"><span data-stu-id="bdd27-129">Specified by rank.</span></span>|<span data-ttu-id="bdd27-130">Volitelně můžete zadat pomocí hranice.</span><span class="sxs-lookup"><span data-stu-id="bdd27-130">Optionally specified by bounds.</span></span>|<span data-ttu-id="bdd27-131">*typ* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="bdd27-131">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="bdd27-132">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="bdd27-132">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="bdd27-133">Neznámé</span><span class="sxs-lookup"><span data-stu-id="bdd27-133">Unknown</span></span>|<span data-ttu-id="bdd27-134">Neznámé</span><span class="sxs-lookup"><span data-stu-id="bdd27-134">Unknown</span></span>|<span data-ttu-id="bdd27-135">Neznámé</span><span class="sxs-lookup"><span data-stu-id="bdd27-135">Unknown</span></span>|<span data-ttu-id="bdd27-136">**System.Array** </span><span class="sxs-lookup"><span data-stu-id="bdd27-136">**System.Array**</span></span>|  
|<span data-ttu-id="bdd27-137">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="bdd27-137">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="bdd27-138">Určený typem.</span><span class="sxs-lookup"><span data-stu-id="bdd27-138">Specified by type.</span></span>|<span data-ttu-id="bdd27-139">1</span><span class="sxs-lookup"><span data-stu-id="bdd27-139">1</span></span>|<span data-ttu-id="bdd27-140">0</span><span class="sxs-lookup"><span data-stu-id="bdd27-140">0</span></span>|<span data-ttu-id="bdd27-141">*typ* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="bdd27-141">*type* **[** *n* **]**</span></span>|  
  
<a name="cpcondefaultmarshalingforarraysanchor2"></a>   
## <a name="unmanaged-arrays"></a><span data-ttu-id="bdd27-142">Nespravované pole</span><span class="sxs-lookup"><span data-stu-id="bdd27-142">Unmanaged Arrays</span></span>  
 <span data-ttu-id="bdd27-143">Nespravované pole jsou bezpečné pole stylu modelu COM nebo pole stylu C s pevným nebo variabilním délkou.</span><span class="sxs-lookup"><span data-stu-id="bdd27-143">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="bdd27-144">Zabezpečeným polím popisující samy sebe, pole, která mají typ, pořadí a rozsah dat přidružené pole.</span><span class="sxs-lookup"><span data-stu-id="bdd27-144">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="bdd27-145">Pole stylu jazyka C jsou jednorozměrné typovaná pole s pevnou dolní mez 0.</span><span class="sxs-lookup"><span data-stu-id="bdd27-145">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="bdd27-146">Zařazovací služby má omezenou podporu pro oba typy polí.</span><span class="sxs-lookup"><span data-stu-id="bdd27-146">The marshaling service has limited support for both types of arrays.</span></span>  
  
<a name="cpcondefaultmarshalingforarraysanchor3"></a>   
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="bdd27-147">Předávání parametrů pole pro kód .NET</span><span class="sxs-lookup"><span data-stu-id="bdd27-147">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="bdd27-148">Pole stylu C a zabezpečeným polím lze předat kód .NET z nespravovaného kódu jako bezpečné pole nebo pole stylu C.</span><span class="sxs-lookup"><span data-stu-id="bdd27-148">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="bdd27-149">Následující tabulka uvádí hodnotu nespravovaný typ a importovaným typem.</span><span class="sxs-lookup"><span data-stu-id="bdd27-149">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="bdd27-150">Nespravovaný typ</span><span class="sxs-lookup"><span data-stu-id="bdd27-150">Unmanaged type</span></span>|<span data-ttu-id="bdd27-151">Importovaný typ.</span><span class="sxs-lookup"><span data-stu-id="bdd27-151">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="bdd27-152">**SafeArray (** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="bdd27-152">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="bdd27-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="bdd27-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="bdd27-154">Pořadí = 1, dolní mez = 0.</span><span class="sxs-lookup"><span data-stu-id="bdd27-154">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="bdd27-155">Velikosti je znám pouze v případě, že součástí spravovaný podpis.</span><span class="sxs-lookup"><span data-stu-id="bdd27-155">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="bdd27-156">Zabezpečeným polím, které nejsou pořadí = 1 nebo dolní mez = 0 nelze zařadit jako **SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="bdd27-156">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="bdd27-157">*Typ\*\*\*]*\* </span><span class="sxs-lookup"><span data-stu-id="bdd27-157">*Type*  **[]**</span></span>|<span data-ttu-id="bdd27-158">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="bdd27-158">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="bdd27-159">Pořadí = 1, dolní mez = 0.</span><span class="sxs-lookup"><span data-stu-id="bdd27-159">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="bdd27-160">Velikosti je znám pouze v případě, že součástí spravovaný podpis.</span><span class="sxs-lookup"><span data-stu-id="bdd27-160">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="bdd27-161">Zabezpečeným polím</span><span class="sxs-lookup"><span data-stu-id="bdd27-161">Safe Arrays</span></span>  
 <span data-ttu-id="bdd27-162">Když bezpečné pole je importována z knihovny typů na sestavení .NET, pole, je převedena na jednorozměrné pole známý typ (například **int**).</span><span class="sxs-lookup"><span data-stu-id="bdd27-162">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="bdd27-163">Stejné pravidel převodu typů, které se vztahují na parametry platí také pro prvky pole.</span><span class="sxs-lookup"><span data-stu-id="bdd27-163">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="bdd27-164">Například bezpečné pole z **BSTR** typy stane spravovaného pole řetězců a bezpečné pole variant stane spravovaného pole objektů.</span><span class="sxs-lookup"><span data-stu-id="bdd27-164">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="bdd27-165">**SAFEARRAY** typ prvku je zachycená z knihovny typů a uložili v **SAFEARRAY** hodnotu <xref:System.Runtime.InteropServices.UnmanagedType> výčtu.</span><span class="sxs-lookup"><span data-stu-id="bdd27-165">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="bdd27-166">Vzhledem k tomu, že z knihovny typů nelze určit počet rozměrů a hranice bezpečné pole, počet rozměrů předpokládá, že je rovno 1 a dolní mez předpokládá, že je rovna 0.</span><span class="sxs-lookup"><span data-stu-id="bdd27-166">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="bdd27-167">Počet rozměrů a hranice musí být definován v spravovaný podpis vytvářených [Importér knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="bdd27-167">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="bdd27-168">Pokud se počet rozměrů předaný metodě v době běhu liší, <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="bdd27-168">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="bdd27-169">Pokud je předán typ pole za běhu liší, <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="bdd27-169">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="bdd27-170">Následující příklad ukazuje zabezpečeným polím v spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="bdd27-170">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="bdd27-171">**Nespravovanému podpisu**</span><span class="sxs-lookup"><span data-stu-id="bdd27-171">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="bdd27-172">**Spravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="bdd27-172">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="bdd27-173">Multidimenzionální nebo nenulovou vázané zabezpečeným polím, může být zařazována do spravovaného kódu, pokud se změní podpis metody vytvářených Tlbimp.exe označující typ elementu **ELEMENT_TYPE_ARRAY** místo **ELEMENT_ TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="bdd27-173">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="bdd27-174">Alternativně můžete použít **/sysarray** přepnout pomocí Tlbimp.exe importujte všechna pole jako <xref:System.Array?displayProperty=nameWithType> objekty.</span><span class="sxs-lookup"><span data-stu-id="bdd27-174">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="bdd27-175">V případech, kde je znám jako multidimenzionální pole předávaný můžete upravit Microsoft kód intermediate language (MSIL) vytvořený pomocí Tlbimp.exe a pak ji znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="bdd27-175">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="bdd27-176">Podrobnosti o tom, jak upravovat kód jazyka MSIL, najdete v článku [přizpůsobení obálek Volatelných za běhu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bdd27-176">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="bdd27-177">Pole stylu C</span><span class="sxs-lookup"><span data-stu-id="bdd27-177">C-Style Arrays</span></span>  
 <span data-ttu-id="bdd27-178">Když pole stylu C je importována z knihovny typů na sestavení .NET, pole, je převedena na **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="bdd27-178">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="bdd27-179">Typ prvku pole je určen z knihovny typů a zachovají během importu.</span><span class="sxs-lookup"><span data-stu-id="bdd27-179">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="bdd27-180">Stejná pravidla převodu, které se vztahují na parametry platí také pro prvky pole.</span><span class="sxs-lookup"><span data-stu-id="bdd27-180">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="bdd27-181">Například pole **LPStr** typy stává polem o **řetězec** typy.</span><span class="sxs-lookup"><span data-stu-id="bdd27-181">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="bdd27-182">Tlbimp.exe zaznamená typ elementu pole a vztahuje <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut parametru.</span><span class="sxs-lookup"><span data-stu-id="bdd27-182">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="bdd27-183">Rozměr pole je považován za rovnat 1.</span><span class="sxs-lookup"><span data-stu-id="bdd27-183">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="bdd27-184">Pokud pořadí je větší než 1, pole se zařadit jako jednorozměrné pole v pořadí preferujícím sloupce.</span><span class="sxs-lookup"><span data-stu-id="bdd27-184">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="bdd27-185">Dolní mez se vždy rovná 0.</span><span class="sxs-lookup"><span data-stu-id="bdd27-185">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="bdd27-186">Knihovny typů mohou obsahovat pole s pevným nebo variabilním délku.</span><span class="sxs-lookup"><span data-stu-id="bdd27-186">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="bdd27-187">Tlbimp.exe můžete importovat pouze pevné délky pole z knihovny typů, protože knihovny typů chybí informace potřebné k zařazení pole proměnné délky.</span><span class="sxs-lookup"><span data-stu-id="bdd27-187">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="bdd27-188">S pevnou délkou pole, velikost naimportované z knihovny typů a zaznamenány **MarshalAsAttribute** , která je použita na parametr.</span><span class="sxs-lookup"><span data-stu-id="bdd27-188">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="bdd27-189">Knihovnu typů obsahující pole proměnné délky, je nutné definovat ručně, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="bdd27-189">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="bdd27-190">**Nespravovanému podpisu**</span><span class="sxs-lookup"><span data-stu-id="bdd27-190">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="bdd27-191">**Spravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="bdd27-191">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="bdd27-192">I když můžete použít **size_is** nebo **length_is –** atributy pole ve zdroji rozhraní Definition Language (IDL) k předání velikosti klientovi definice jazyka MIDL (Microsoft Interface) Kompilátor nešíří tyto informace do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="bdd27-192">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="bdd27-193">Nainstalovat bez mého velikosti, nelze zařadit zprostředkovatele komunikace s objekty zařazování služby prvků pole.</span><span class="sxs-lookup"><span data-stu-id="bdd27-193">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="bdd27-194">Pole proměnné délky v důsledku toho jsou naimportované jako argumenty odkazu.</span><span class="sxs-lookup"><span data-stu-id="bdd27-194">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="bdd27-195">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bdd27-195">For example:</span></span>  
  
 <span data-ttu-id="bdd27-196">**Nespravovanému podpisu**</span><span class="sxs-lookup"><span data-stu-id="bdd27-196">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="bdd27-197">**Spravovaný podpis**</span><span class="sxs-lookup"><span data-stu-id="bdd27-197">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="bdd27-198">Aby zařazování odvozovalo můžete poskytnout velikost pole úpravou Microsoft kód intermediate language (MSIL) vytvořený pomocí Tlbimp.exe a poté opětovné kompilace.</span><span class="sxs-lookup"><span data-stu-id="bdd27-198">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="bdd27-199">Podrobnosti o tom, jak upravovat kód jazyka MSIL, najdete v článku [přizpůsobení obálek Volatelných za běhu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="bdd27-199">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="bdd27-200">Chcete-li určit počet prvků v poli, použijte <xref:System.Runtime.InteropServices.MarshalAsAttribute> typ pro parametr pole definici spravované metody v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="bdd27-200">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
-   <span data-ttu-id="bdd27-201">Určete další parametr, který obsahuje počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="bdd27-201">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="bdd27-202">Parametry jsou označeny pozici, počínaje první parametr jako číslo 0.</span><span class="sxs-lookup"><span data-stu-id="bdd27-202">The parameters are identified by position, starting with the first parameter as number 0.</span></span>     
  
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
  
-   <span data-ttu-id="bdd27-203">Definujte velikost pole jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="bdd27-203">Define the size of the array as a constant.</span></span> <span data-ttu-id="bdd27-204">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bdd27-204">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="bdd27-205">Při zařazování polí z nespravovaného kódu pro spravovaný kód, aby zařazování odvozovalo kontroluje, **MarshalAsAttribute** spojené s parametrem určit velikost pole.</span><span class="sxs-lookup"><span data-stu-id="bdd27-205">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="bdd27-206">Pokud nezadáte velikost pole, je zařadit pouze jeden element.</span><span class="sxs-lookup"><span data-stu-id="bdd27-206">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdd27-207">**MarshalAsAttribute** nemá žádný vliv na zařazování spravované pole na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="bdd27-207">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="bdd27-208">V tomto směru velikost pole je určeno zkoumání.</span><span class="sxs-lookup"><span data-stu-id="bdd27-208">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="bdd27-209">Neexistuje žádný způsob, jak zařadit podmnožinu spravovaného pole.</span><span class="sxs-lookup"><span data-stu-id="bdd27-209">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="bdd27-210">Interoperační zařazovač používá **CoTaskMemAlloc** a **CoTaskMemFree** metody přidělení a načítat paměti.</span><span class="sxs-lookup"><span data-stu-id="bdd27-210">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="bdd27-211">Přidělení paměti provedené nespravovaný kód musí taky používat tyto metody.</span><span class="sxs-lookup"><span data-stu-id="bdd27-211">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
<a name="cpcondefaultmarshalingforarraysanchor4"></a>   
## <a name="passing-arrays-to-com"></a><span data-ttu-id="bdd27-212">Předávání polí do modelu COM</span><span class="sxs-lookup"><span data-stu-id="bdd27-212">Passing Arrays to COM</span></span>  
 <span data-ttu-id="bdd27-213">Všechny typy spravovaného pole může být předán nespravovanému kódu ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="bdd27-213">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="bdd27-214">V závislosti na spravovaný typ a atributy použité na jeho pole je přístupná jako bezpečné pole nebo pole stylu C, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="bdd27-214">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="bdd27-215">Spravovaná pole</span><span class="sxs-lookup"><span data-stu-id="bdd27-215">Managed array type</span></span>|<span data-ttu-id="bdd27-216">Exportovat jako</span><span class="sxs-lookup"><span data-stu-id="bdd27-216">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="bdd27-217">**ELEMENT_TYPE_SZARRAY** **\<** *typu* **>**</span><span class="sxs-lookup"><span data-stu-id="bdd27-217">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="bdd27-218"><xref:System.Runtime.InteropServices.UnmanagedType> **. SafeArray (** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="bdd27-218"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="bdd27-219">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="bdd27-219">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="bdd27-220">Typ je poskytován v podpisu.</span><span class="sxs-lookup"><span data-stu-id="bdd27-220">Type is provided in the signature.</span></span> <span data-ttu-id="bdd27-221">Pořadí je vždy 1, dolní mez je vždy 0.</span><span class="sxs-lookup"><span data-stu-id="bdd27-221">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="bdd27-222">Velikost je vždy známý v době běhu.</span><span class="sxs-lookup"><span data-stu-id="bdd27-222">Size is always known at run time.</span></span>|  
|<span data-ttu-id="bdd27-223">**ELEMENT_TYPE_ARRAY** **\<** *typ* **>** **\<** *pořadí* **>**[**\<** *hranice* **>**]</span><span class="sxs-lookup"><span data-stu-id="bdd27-223">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="bdd27-224">**UnmanagedType.SafeArray (** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="bdd27-224">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="bdd27-225">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="bdd27-225">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="bdd27-226">Typ, řadit, hranice jsou k dispozici v podpisu.</span><span class="sxs-lookup"><span data-stu-id="bdd27-226">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="bdd27-227">Velikost je vždy známý v době běhu.</span><span class="sxs-lookup"><span data-stu-id="bdd27-227">Size is always known at run time.</span></span>|  
|<span data-ttu-id="bdd27-228">**ZA ŘETĚZCEM ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span><span class="sxs-lookup"><span data-stu-id="bdd27-228">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span></span>|<span data-ttu-id="bdd27-229">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="bdd27-229">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="bdd27-230">**UnmanagedType.SafeArray (** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="bdd27-230">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="bdd27-231">Typ, hodnocení, hranice a velikosti jsou vždy známý v době běhu.</span><span class="sxs-lookup"><span data-stu-id="bdd27-231">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="bdd27-232">Existuje omezení v automatizace OLE týkající se pole struktur, které obsahují LPSTR, LPWSTR nebo.</span><span class="sxs-lookup"><span data-stu-id="bdd27-232">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="bdd27-233">Proto **řetězec** pole mají být zařazena jako **UnmanagedType.BSTR**.</span><span class="sxs-lookup"><span data-stu-id="bdd27-233">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="bdd27-234">V opačném případě bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="bdd27-234">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="elementtypeszarray"></a><span data-ttu-id="bdd27-235">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="bdd27-235">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="bdd27-236">Pokud metoda obsahuje **ELEMENT_TYPE_SZARRAY** parametr (jednorozměrné pole) je exportována z .NET sestavení na knihovnu typů, protože parametr pole je převedena na **SAFEARRAY** daného typu.</span><span class="sxs-lookup"><span data-stu-id="bdd27-236">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="bdd27-237">Stejný převod pravidla se vztahují na typy prvků pole.</span><span class="sxs-lookup"><span data-stu-id="bdd27-237">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="bdd27-238">Obsah spravovaného pole se automaticky zkopírují ze spravované paměti do **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="bdd27-238">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="bdd27-239">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bdd27-239">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="bdd27-240">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="bdd27-240">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="bdd27-241">Nespravovanému podpisu</span><span class="sxs-lookup"><span data-stu-id="bdd27-241">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="bdd27-242">Řád objektu zabezpečeným polím je vždy 1 a dolní mez je vždy 0.</span><span class="sxs-lookup"><span data-stu-id="bdd27-242">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="bdd27-243">Velikost je určena v době běhu velikostí spravovaného pole předávána.</span><span class="sxs-lookup"><span data-stu-id="bdd27-243">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="bdd27-244">Pole můžete také zařadit jako pole stylu jazyka C pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="bdd27-244">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="bdd27-245">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bdd27-245">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="bdd27-246">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="bdd27-246">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="bdd27-247">Nespravovanému podpisu</span><span class="sxs-lookup"><span data-stu-id="bdd27-247">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="bdd27-248">I když zařazování má délku informace potřebné k zařazení pole, délka pole je obvykle předán jako samostatné argument k předání délka volaného.</span><span class="sxs-lookup"><span data-stu-id="bdd27-248">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="elementtypearray"></a><span data-ttu-id="bdd27-249">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="bdd27-249">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="bdd27-250">Pokud metoda obsahuje **ELEMENT_TYPE_ARRAY** parametr se exportuje z .NET sestavení na knihovnu typů, je parametr pole převedena na **SAFEARRAY** daného typu.</span><span class="sxs-lookup"><span data-stu-id="bdd27-250">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="bdd27-251">Obsah spravovaného pole se automaticky zkopírují ze spravované paměti do **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="bdd27-251">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="bdd27-252">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bdd27-252">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="bdd27-253">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="bdd27-253">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="bdd27-254">Nespravovanému podpisu</span><span class="sxs-lookup"><span data-stu-id="bdd27-254">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="bdd27-255">Počet rozměrů, velikost a hranice zabezpečeným polím jsou určeny v době běhu vlastnosti spravovaného pole.</span><span class="sxs-lookup"><span data-stu-id="bdd27-255">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="bdd27-256">Pole můžete také zařadit jako pole stylu C použitím <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="bdd27-256">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="bdd27-257">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bdd27-257">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="bdd27-258">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="bdd27-258">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="bdd27-259">Nespravovanému podpisu</span><span class="sxs-lookup"><span data-stu-id="bdd27-259">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="bdd27-260">Vnořená pole nelze zařadit.</span><span class="sxs-lookup"><span data-stu-id="bdd27-260">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="bdd27-261">Například následující podpis dojde k chybě při exportu s [Exportér knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="bdd27-261">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="bdd27-262">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="bdd27-262">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a><span data-ttu-id="bdd27-263">Za řetězcem ELEMENT_TYPE_CLASS \<System.Array ></span><span class="sxs-lookup"><span data-stu-id="bdd27-263">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="bdd27-264">Pokud metoda obsahuje <xref:System.Array?displayProperty=nameWithType> parametr se exportuje z .NET sestavení na knihovnu typů, je parametr pole převedena na **_pole** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bdd27-264">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="bdd27-265">Obsah spravovaného pole jsou přístupné pouze prostřednictvím metody a vlastnosti **_pole** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bdd27-265">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="bdd27-266">**Objekt System.Array** můžete také zařadit jako **SAFEARRAY** pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="bdd27-266">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="bdd27-267">Při zařazení jako bezpečné pole prvků pole, jsou zařazeny jako variant.</span><span class="sxs-lookup"><span data-stu-id="bdd27-267">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="bdd27-268">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bdd27-268">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="bdd27-269">Spravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="bdd27-269">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="bdd27-270">Nespravovanému podpisu</span><span class="sxs-lookup"><span data-stu-id="bdd27-270">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="bdd27-271">Pole v rámci struktury</span><span class="sxs-lookup"><span data-stu-id="bdd27-271">Arrays within Structures</span></span>  
 <span data-ttu-id="bdd27-272">Nespravované struktury mohou obsahovat vloženého pole.</span><span class="sxs-lookup"><span data-stu-id="bdd27-272">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="bdd27-273">Ve výchozím nastavení jsou zařazeny tyto vložené pole jako SAFEARRAY.</span><span class="sxs-lookup"><span data-stu-id="bdd27-273">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="bdd27-274">V následujícím příkladu `s1` je vložené pole, která je přidělena přímo v rámci struktury samotné.</span><span class="sxs-lookup"><span data-stu-id="bdd27-274">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="bdd27-275">Nespravované reprezentace</span><span class="sxs-lookup"><span data-stu-id="bdd27-275">Unmanaged representation</span></span>  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="bdd27-276">Pole může být zařazována jako <xref:System.Runtime.InteropServices.UnmanagedType>, což vyžaduje, abyste nastavili <xref:System.Runtime.InteropServices.MarshalAsAttribute> pole.</span><span class="sxs-lookup"><span data-stu-id="bdd27-276">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="bdd27-277">Velikost lze nastavit pouze jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="bdd27-277">The size can be set only as a constant.</span></span> <span data-ttu-id="bdd27-278">Následující kód ukazuje příslušné spravované definici `MyStruct`.</span><span class="sxs-lookup"><span data-stu-id="bdd27-278">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bdd27-279">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bdd27-279">See also</span></span>
- [<span data-ttu-id="bdd27-280">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="bdd27-280">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="bdd27-281">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="bdd27-281">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="bdd27-282">[Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bdd27-282">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="bdd27-283">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="bdd27-283">Copying and Pinning</span></span>](copying-and-pinning.md)
