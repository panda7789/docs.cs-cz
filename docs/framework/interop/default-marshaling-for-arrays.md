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
ms.openlocfilehash: b05ac1016710109110c3ff9d0d318a71fe0827f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393147"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="1db06-102">Výchozí zařazování pro pole</span><span class="sxs-lookup"><span data-stu-id="1db06-102">Default Marshaling for Arrays</span></span>
<span data-ttu-id="1db06-103">V aplikaci, která obsahuje jenom spravovaného kódu modul common language runtime předá typy polí jako vstupně -výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="1db06-103">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="1db06-104">Naproti tomu spolupráce vláken předá pole jako parametry ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="1db06-104">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="1db06-105">S [Připnutí optimalizace](copying-and-pinning.md), pole přenositelné můžou zdánlivě pracovat jako ve vstupně -výstupnímu parametru při interakci s objekty ve stejném typu apartment.</span><span class="sxs-lookup"><span data-stu-id="1db06-105">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="1db06-106">Ale pokud později exportovat kód do knihovny typů sloužící ke generování proxy serveru mezi počítači a že knihovna se používá k zařazování voláními napříč apartment, volání obnovit na hodnotu true v parametru chování.</span><span class="sxs-lookup"><span data-stu-id="1db06-106">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="1db06-107">Pole jsou svou povahou komplexní a rozdíly mezi spravovanými a nespravovanými pole zaručit informace než jiné nepřenositelné typy.</span><span class="sxs-lookup"><span data-stu-id="1db06-107">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span> <span data-ttu-id="1db06-108">Toto téma obsahuje následující informace na zařazování pole:</span><span class="sxs-lookup"><span data-stu-id="1db06-108">This topic provides the following information on marshaling arrays:</span></span>  
  
-   [<span data-ttu-id="1db06-109">Spravovaná pole</span><span class="sxs-lookup"><span data-stu-id="1db06-109">Managed Arrays</span></span>](#cpcondefaultmarshalingforarraysanchor1)  
  
-   [<span data-ttu-id="1db06-110">Nespravované pole</span><span class="sxs-lookup"><span data-stu-id="1db06-110">Unmanaged Arrays</span></span>](#cpcondefaultmarshalingforarraysanchor2)  
  
-   [<span data-ttu-id="1db06-111">Předávání parametrů pole pro kód .NET</span><span class="sxs-lookup"><span data-stu-id="1db06-111">Passing Array Parameters to .NET Code</span></span>](#cpcondefaultmarshalingforarraysanchor3)  
  
-   [<span data-ttu-id="1db06-112">Předávání polí do modelu COM</span><span class="sxs-lookup"><span data-stu-id="1db06-112">Passing Arrays to COM</span></span>](#cpcondefaultmarshalingforarraysanchor4)  
  
<a name="cpcondefaultmarshalingforarraysanchor1"></a>   
## <a name="managed-arrays"></a><span data-ttu-id="1db06-113">Spravovaná pole</span><span class="sxs-lookup"><span data-stu-id="1db06-113">Managed Arrays</span></span>  
 <span data-ttu-id="1db06-114">Spravovaná pole, které mohou být různé typy; ale <xref:System.Array?displayProperty=nameWithType> třída je základní třída všech typů pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-114">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="1db06-115">**System.Array** třída má vlastnosti pro určení pořadí, délku a dolní a horní meze pole, jakož i metody pro přístup k, řazení, hledání, kopírování a vytvoření pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-115">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="1db06-116">Tyto typy polí je dynamická a nemají odpovídající statické typem definovaným v knihovně základní třídy.</span><span class="sxs-lookup"><span data-stu-id="1db06-116">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="1db06-117">Je vhodné zamyslet nad každou kombinaci typ elementu a pořadí jako odlišné typ pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-117">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="1db06-118">Jednorozměrné pole celých čísel je proto jiného typu než jednorozměrné pole dvojité typů.</span><span class="sxs-lookup"><span data-stu-id="1db06-118">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="1db06-119">Podobně se liší od jednorozměrné pole celých čísel na dvourozměrné pole celých čísel.</span><span class="sxs-lookup"><span data-stu-id="1db06-119">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="1db06-120">Při porovnávání typů, nejsou považovány za hranice pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-120">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="1db06-121">Jak ukazuje následující tabulka, všechny instance spravovaného pole musí být typu konkrétní elementu, pořadí a dolní mez.</span><span class="sxs-lookup"><span data-stu-id="1db06-121">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="1db06-122">Spravovaný typ pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-122">Managed array type</span></span>|<span data-ttu-id="1db06-123">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="1db06-123">Element type</span></span>|<span data-ttu-id="1db06-124">Pořadí</span><span class="sxs-lookup"><span data-stu-id="1db06-124">Rank</span></span>|<span data-ttu-id="1db06-125">Dolní mez</span><span class="sxs-lookup"><span data-stu-id="1db06-125">Lower bound</span></span>|<span data-ttu-id="1db06-126">Zápis podpis</span><span class="sxs-lookup"><span data-stu-id="1db06-126">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="1db06-127">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="1db06-127">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="1db06-128">Zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="1db06-128">Specified by type.</span></span>|<span data-ttu-id="1db06-129">Zadaný pořadí.</span><span class="sxs-lookup"><span data-stu-id="1db06-129">Specified by rank.</span></span>|<span data-ttu-id="1db06-130">Volitelně zadaný rozsah.</span><span class="sxs-lookup"><span data-stu-id="1db06-130">Optionally specified by bounds.</span></span>|<span data-ttu-id="1db06-131">*typ* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="1db06-131">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="1db06-132">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="1db06-132">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="1db06-133">Neznámé</span><span class="sxs-lookup"><span data-stu-id="1db06-133">Unknown</span></span>|<span data-ttu-id="1db06-134">Neznámé</span><span class="sxs-lookup"><span data-stu-id="1db06-134">Unknown</span></span>|<span data-ttu-id="1db06-135">Neznámé</span><span class="sxs-lookup"><span data-stu-id="1db06-135">Unknown</span></span>|<span data-ttu-id="1db06-136">**System.Array**</span><span class="sxs-lookup"><span data-stu-id="1db06-136">**System.Array**</span></span>|  
|<span data-ttu-id="1db06-137">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="1db06-137">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="1db06-138">Zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="1db06-138">Specified by type.</span></span>|<span data-ttu-id="1db06-139">1</span><span class="sxs-lookup"><span data-stu-id="1db06-139">1</span></span>|<span data-ttu-id="1db06-140">0</span><span class="sxs-lookup"><span data-stu-id="1db06-140">0</span></span>|<span data-ttu-id="1db06-141">*typ* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="1db06-141">*type* **[** *n* **]**</span></span>|  
  
<a name="cpcondefaultmarshalingforarraysanchor2"></a>   
## <a name="unmanaged-arrays"></a><span data-ttu-id="1db06-142">Nespravované pole</span><span class="sxs-lookup"><span data-stu-id="1db06-142">Unmanaged Arrays</span></span>  
 <span data-ttu-id="1db06-143">Nespravované pole je COM stylu bezpečné pole nebo pole stylu jazyka C s pevnou velikostí, nebo proměnnou délkou.</span><span class="sxs-lookup"><span data-stu-id="1db06-143">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="1db06-144">Bezpečné pole jsou popisující samy sebe pole, které zajišťují typu, pořadí a rozsah dat přidružené žádné pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-144">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="1db06-145">Pole stylu jazyka C jsou jednorozměrné typovaná pole s pevnou dolní mez 0.</span><span class="sxs-lookup"><span data-stu-id="1db06-145">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="1db06-146">Služba zařazování má omezenou podporu pro oba typy polí.</span><span class="sxs-lookup"><span data-stu-id="1db06-146">The marshaling service has limited support for both types of arrays.</span></span>  
  
<a name="cpcondefaultmarshalingforarraysanchor3"></a>   
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="1db06-147">Předávání parametrů pole pro kód .NET</span><span class="sxs-lookup"><span data-stu-id="1db06-147">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="1db06-148">Pole stylu jazyka C a bezpečné pole lze předat kód .NET z nespravovaného kódu jako bezpečné pole nebo pole ve stylu jazyka.</span><span class="sxs-lookup"><span data-stu-id="1db06-148">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="1db06-149">Následující tabulka uvádí nespravovaný typ hodnoty a typ importované.</span><span class="sxs-lookup"><span data-stu-id="1db06-149">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="1db06-150">Nespravovaný typ</span><span class="sxs-lookup"><span data-stu-id="1db06-150">Unmanaged type</span></span>|<span data-ttu-id="1db06-151">Importovaný typ</span><span class="sxs-lookup"><span data-stu-id="1db06-151">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="1db06-152">**SafeArray (** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="1db06-152">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="1db06-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="1db06-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="1db06-154">Pořadí = 1, dolní mez = 0.</span><span class="sxs-lookup"><span data-stu-id="1db06-154">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="1db06-155">Velikost je známý jenom v případě, že součástí spravované podpis.</span><span class="sxs-lookup"><span data-stu-id="1db06-155">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="1db06-156">Bezpečné pole, které nejsou rank = 1, nebo dolní mez = 0 nelze zařadit jako **SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="1db06-156">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="1db06-157">*Typ***]**</span><span class="sxs-lookup"><span data-stu-id="1db06-157">*Type*  **[]**</span></span>|<span data-ttu-id="1db06-158">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="1db06-158">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="1db06-159">Pořadí = 1, dolní mez = 0.</span><span class="sxs-lookup"><span data-stu-id="1db06-159">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="1db06-160">Velikost je známý jenom v případě, že součástí spravované podpis.</span><span class="sxs-lookup"><span data-stu-id="1db06-160">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="1db06-161">Bezpečné pole</span><span class="sxs-lookup"><span data-stu-id="1db06-161">Safe Arrays</span></span>  
 <span data-ttu-id="1db06-162">Při importu bezpečným polím z knihovny typů pro sestavení .NET pole jsou převedeny na jednorozměrné pole známé typu (například **int**).</span><span class="sxs-lookup"><span data-stu-id="1db06-162">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="1db06-163">Stejné pravidel převodu typů, které se vztahují na parametry platí také pro elementy pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-163">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="1db06-164">Například bezpečným polím z **BSTR** typy bude spravované pole řetězců a bezpečným polím variant bude spravované pole objektů.</span><span class="sxs-lookup"><span data-stu-id="1db06-164">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="1db06-165">**SAFEARRAY** zaznamenat z knihovny typů a uložit v typu elementu **SAFEARRAY** hodnotu <xref:System.Runtime.InteropServices.UnmanagedType> výčtu.</span><span class="sxs-lookup"><span data-stu-id="1db06-165">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="1db06-166">Protože pořadí a hranice bezpečné pole nelze určit z knihovny typů, pořadí se předpokládá, že rovno 1 a dolní hranice se předpokládá, že rovna 0.</span><span class="sxs-lookup"><span data-stu-id="1db06-166">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="1db06-167">Pořadí a rozsah musí být definován v spravované podpis vyprodukované [Importér knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="1db06-167">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="1db06-168">Pokud se liší pořadí předaný metodě za běhu, <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1db06-168">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="1db06-169">Pokud v době běhu byl předán typ pole se liší, <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1db06-169">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="1db06-170">Následující příklad ukazuje bezpečné pole v spravovanými a nespravovanými kódu.</span><span class="sxs-lookup"><span data-stu-id="1db06-170">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="1db06-171">**Nespravované podpis**</span><span class="sxs-lookup"><span data-stu-id="1db06-171">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="1db06-172">**Spravované podpis**</span><span class="sxs-lookup"><span data-stu-id="1db06-172">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="1db06-173">Multidimenzionální nebo nenulové hodnoty svázané bezpečné pole, může být zařazeno do spravovaného kódu, pokud metoda podpis vyprodukované Tlbimp.exe je upravit tak, aby označuje typ elementu **ELEMENT_TYPE_ARRAY** místo **ELEMENT_ TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="1db06-173">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="1db06-174">Alternativně můžete použít **/sysarray** přepínač s Tlbimp.exe k importu všech polí jako <xref:System.Array?displayProperty=nameWithType> objekty.</span><span class="sxs-lookup"><span data-stu-id="1db06-174">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="1db06-175">V případech, kde je znám být multidimenzionální pole předávány můžete upravit Microsoft (MSIL intermediate language) kódu vytvořeného pomocí Tlbimp.exe a pak ji znovu zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="1db06-175">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="1db06-176">Podrobnosti o tom, jak upravit MSIL kódu najdete v tématu [přizpůsobení běhové obálky s možností](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1db06-176">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="1db06-177">Pole stylu jazyka C</span><span class="sxs-lookup"><span data-stu-id="1db06-177">C-Style Arrays</span></span>  
 <span data-ttu-id="1db06-178">Pokud pole ve stylu jazyka je importované z knihovny typů do sestavení .NET, pole je převést na **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="1db06-178">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="1db06-179">Typ elementu pole je určen z knihovny typů a zachovají během importu.</span><span class="sxs-lookup"><span data-stu-id="1db06-179">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="1db06-180">Stejná pravidla převodu, které se vztahují na parametry platí také pro elementy pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-180">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="1db06-181">Například pole **LPStr** typy stane pole **řetězec** typy.</span><span class="sxs-lookup"><span data-stu-id="1db06-181">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="1db06-182">Tlbimp.exe zaznamená typ elementu pole a použije <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut parametr.</span><span class="sxs-lookup"><span data-stu-id="1db06-182">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="1db06-183">Pole pořadí se předpokládá, že rovnat 1.</span><span class="sxs-lookup"><span data-stu-id="1db06-183">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="1db06-184">Pokud pořadí je větší než 1, je pole zařazené jako jednorozměrné pole uváděnými sloupce.</span><span class="sxs-lookup"><span data-stu-id="1db06-184">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="1db06-185">Dolní mez se vždy rovná 0.</span><span class="sxs-lookup"><span data-stu-id="1db06-185">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="1db06-186">Knihovny typů může obsahovat pole Délka pevné nebo proměnné.</span><span class="sxs-lookup"><span data-stu-id="1db06-186">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="1db06-187">Tlbimp.exe můžete importovat pouze pevnou délkou pole z knihovny typů, protože knihovny typů neobsahují informace potřebné pro zařazování proměnlivou délkou pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-187">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="1db06-188">S pevnou délkou pole velikost naimportované z knihovny typů a zachyceného **MarshalAsAttribute** který se použije pro parametr.</span><span class="sxs-lookup"><span data-stu-id="1db06-188">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="1db06-189">Knihovny typů s proměnlivou délkou pole, je nutné zadat ručně, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1db06-189">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="1db06-190">**Nespravované podpis**</span><span class="sxs-lookup"><span data-stu-id="1db06-190">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="1db06-191">**Spravované podpis**</span><span class="sxs-lookup"><span data-stu-id="1db06-191">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="1db06-192">I když můžete použít **size_is –** nebo **length_is –** atributy na pole ve zdroji definice jazyka IDL (Interface) pro vyjádření velikost ke klientovi, jazyk definice rozhraní Microsoft (MIDL) kompilátoru nešířily tyto informace do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="1db06-192">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="1db06-193">Aniž by věděly, velikost, nelze zprostředkovatel komunikace s objekty zařazování služby zařazování prvků pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-193">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="1db06-194">V důsledku toho se importují proměnlivou délkou pole jako argumenty odkaz.</span><span class="sxs-lookup"><span data-stu-id="1db06-194">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="1db06-195">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1db06-195">For example:</span></span>  
  
 <span data-ttu-id="1db06-196">**Nespravované podpis**</span><span class="sxs-lookup"><span data-stu-id="1db06-196">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="1db06-197">**Spravované podpis**</span><span class="sxs-lookup"><span data-stu-id="1db06-197">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="1db06-198">Zařazování můžete poskytnout velikost pole úpravou Microsoft (MSIL intermediate language) kódu vytvořeného pomocí Tlbimp.exe a pak kompilovat znovu.</span><span class="sxs-lookup"><span data-stu-id="1db06-198">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="1db06-199">Podrobnosti o tom, jak upravit MSIL kódu najdete v tématu [přizpůsobení běhové obálky s možností](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1db06-199">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100)).</span></span> <span data-ttu-id="1db06-200">Pokud chcete zadat počet prvků v poli, použít <xref:System.Runtime.InteropServices.MarshalAsAttribute> typ pro parametr pole spravované metoda definice v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="1db06-200">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
-   <span data-ttu-id="1db06-201">Identifikujte jiný parametr, který obsahuje počet prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="1db06-201">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="1db06-202">Parametry jsou identifikovány pozice, počínaje první parametr jako číslo 0.</span><span class="sxs-lookup"><span data-stu-id="1db06-202">The parameters are identified by position, starting with the first parameter as number 0.</span></span>     
  
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
  
-   <span data-ttu-id="1db06-203">Zadejte velikost pole jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="1db06-203">Define the size of the array as a constant.</span></span> <span data-ttu-id="1db06-204">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1db06-204">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="1db06-205">Při zařazování polí z nespravovaného kódu do spravovaného kódu, zkontroluje zařazování **MarshalAsAttribute** přidružené parametr k určení velikosti pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-205">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="1db06-206">Pokud není zadán velikost pole, je zařadit pouze jeden element.</span><span class="sxs-lookup"><span data-stu-id="1db06-206">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1db06-207">**MarshalAsAttribute** nemá žádný vliv na zařazování spravované pole na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="1db06-207">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="1db06-208">Velikost pole v tomto směru, je dáno prozkoumání.</span><span class="sxs-lookup"><span data-stu-id="1db06-208">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="1db06-209">Neexistuje žádný způsob, jak zařazování podmnožinu spravovaného pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-209">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="1db06-210">Používá zprostředkovatele komunikace s objekty vláken **CoTaskMemAlloc** a **CoTaskMemFree** metody přidělit a načtení paměti.</span><span class="sxs-lookup"><span data-stu-id="1db06-210">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="1db06-211">Přidělení paměti provádí nespravovaného kódu musíte taky použít tyto metody.</span><span class="sxs-lookup"><span data-stu-id="1db06-211">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
<a name="cpcondefaultmarshalingforarraysanchor4"></a>   
## <a name="passing-arrays-to-com"></a><span data-ttu-id="1db06-212">Předávání polí do modelu COM</span><span class="sxs-lookup"><span data-stu-id="1db06-212">Passing Arrays to COM</span></span>  
 <span data-ttu-id="1db06-213">Všechny typy spravované pole lze předat nespravovaného kódu ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="1db06-213">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="1db06-214">V závislosti na spravovaný typ a atributy použité na jeho pole můžou mít přístup bezpečné pole nebo pole stylu jazyka C, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="1db06-214">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="1db06-215">Spravovaný typ pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-215">Managed array type</span></span>|<span data-ttu-id="1db06-216">Exportovat jako</span><span class="sxs-lookup"><span data-stu-id="1db06-216">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="1db06-217">**ELEMENT_TYPE_SZARRAY** **\<** *typu* **>**</span><span class="sxs-lookup"><span data-stu-id="1db06-217">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="1db06-218"><xref:System.Runtime.InteropServices.UnmanagedType> **. SafeArray (** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="1db06-218"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="1db06-219">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="1db06-219">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="1db06-220">Typ je součástí podpis.</span><span class="sxs-lookup"><span data-stu-id="1db06-220">Type is provided in the signature.</span></span> <span data-ttu-id="1db06-221">Pořadí je vždy 1, dolní mez je vždy 0.</span><span class="sxs-lookup"><span data-stu-id="1db06-221">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="1db06-222">Velikost se vždy označuje za běhu.</span><span class="sxs-lookup"><span data-stu-id="1db06-222">Size is always known at run time.</span></span>|  
|<span data-ttu-id="1db06-223">**ELEMENT_TYPE_ARRAY** **\<** *typ* **>** **\<** *pořadí* **>**[**\<** *hranice* **>**]</span><span class="sxs-lookup"><span data-stu-id="1db06-223">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="1db06-224">**UnmanagedType.SafeArray (** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="1db06-224">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="1db06-225">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="1db06-225">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="1db06-226">Rank, hranice typu, jsou uvedeny v podpis.</span><span class="sxs-lookup"><span data-stu-id="1db06-226">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="1db06-227">Velikost se vždy označuje za běhu.</span><span class="sxs-lookup"><span data-stu-id="1db06-227">Size is always known at run time.</span></span>|  
|<span data-ttu-id="1db06-228">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span><span class="sxs-lookup"><span data-stu-id="1db06-228">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span></span>|<span data-ttu-id="1db06-229">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="1db06-229">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="1db06-230">**UnmanagedType.SafeArray (** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="1db06-230">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="1db06-231">Typ, pořadí, rozsah a velikosti jsou vždy známé za běhu.</span><span class="sxs-lookup"><span data-stu-id="1db06-231">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="1db06-232">Existuje omezení v automatizace OLE týkající se pole struktur, které obsahují LPSTR nebo LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="1db06-232">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="1db06-233">Proto **řetězec** pole mají být zařazena jako **UnmanagedType.BSTR**.</span><span class="sxs-lookup"><span data-stu-id="1db06-233">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="1db06-234">Jinak bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="1db06-234">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="elementtypeszarray"></a><span data-ttu-id="1db06-235">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="1db06-235">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="1db06-236">Když metoda obsahuje **ELEMENT_TYPE_SZARRAY** parametr (jednorozměrné pole) se exportují z sestavení .NET do knihovny typů, parametr pole jsou převedeny na **SAFEARRAY** daného typu.</span><span class="sxs-lookup"><span data-stu-id="1db06-236">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="1db06-237">Stejná pravidla převodu platí pro pole typů elementů.</span><span class="sxs-lookup"><span data-stu-id="1db06-237">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="1db06-238">Obsah bude spravované pole se automaticky zkopírují ze spravované paměti do **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="1db06-238">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="1db06-239">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1db06-239">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="1db06-240">Spravované podpis</span><span class="sxs-lookup"><span data-stu-id="1db06-240">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="1db06-241">Nespravované podpis</span><span class="sxs-lookup"><span data-stu-id="1db06-241">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="1db06-242">Pořadí bezpečné pole je vždy 1 a dolní hranice je vždy 0.</span><span class="sxs-lookup"><span data-stu-id="1db06-242">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="1db06-243">Velikost je určena v době běhu velikostí spravované pole předávány.</span><span class="sxs-lookup"><span data-stu-id="1db06-243">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="1db06-244">Pole můžete také zařazeno jako pole ve stylu jazyka C pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="1db06-244">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="1db06-245">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1db06-245">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="1db06-246">Spravované podpis</span><span class="sxs-lookup"><span data-stu-id="1db06-246">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="1db06-247">Nespravované podpis</span><span class="sxs-lookup"><span data-stu-id="1db06-247">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="1db06-248">I když zařazování má délku informace potřebné pro zařazování pole, délka pole je obvykle předat jako samostatné argument pro vyjádření délka volaného.</span><span class="sxs-lookup"><span data-stu-id="1db06-248">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="elementtypearray"></a><span data-ttu-id="1db06-249">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="1db06-249">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="1db06-250">Když metoda obsahuje **ELEMENT_TYPE_ARRAY** parametr exportují z sestavení .NET do knihovny typů, parametr pole jsou převedeny na **SAFEARRAY** daného typu.</span><span class="sxs-lookup"><span data-stu-id="1db06-250">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="1db06-251">Obsah bude spravované pole se automaticky zkopírují ze spravované paměti do **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="1db06-251">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="1db06-252">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1db06-252">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="1db06-253">Spravované podpis</span><span class="sxs-lookup"><span data-stu-id="1db06-253">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="1db06-254">Nespravované podpis</span><span class="sxs-lookup"><span data-stu-id="1db06-254">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="1db06-255">Pořadí, velikost a rozsah bezpečné polí jsou určena v době běhu charakteristikami spravované pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-255">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="1db06-256">Pole můžete také zařazeno jako pole ve stylu jazyka C s použitím <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="1db06-256">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="1db06-257">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1db06-257">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="1db06-258">Spravované podpis</span><span class="sxs-lookup"><span data-stu-id="1db06-258">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="1db06-259">Nespravované podpis</span><span class="sxs-lookup"><span data-stu-id="1db06-259">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="1db06-260">Vnořená pole nelze zařadit.</span><span class="sxs-lookup"><span data-stu-id="1db06-260">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="1db06-261">Například následující podpis, vygeneruje se chyba při exportu se [Exportér knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="1db06-261">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="1db06-262">Spravované podpis</span><span class="sxs-lookup"><span data-stu-id="1db06-262">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a><span data-ttu-id="1db06-263">ELEMENT_TYPE_CLASS \<System.Array ></span><span class="sxs-lookup"><span data-stu-id="1db06-263">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="1db06-264">Když metoda obsahuje <xref:System.Array?displayProperty=nameWithType> parametr exportují z sestavení .NET do knihovny typů, parametr pole jsou převedeny na **_Array** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1db06-264">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="1db06-265">Obsah bude spravované pole je přístupné pouze prostřednictvím metody a vlastnosti **_Array** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1db06-265">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="1db06-266">**System.Array** můžete také zařazené jako **SAFEARRAY** pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="1db06-266">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="1db06-267">Když zařazené jako bezpečné pole, elementy pole jsou zařazené jako varianty.</span><span class="sxs-lookup"><span data-stu-id="1db06-267">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="1db06-268">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1db06-268">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="1db06-269">Spravované podpis</span><span class="sxs-lookup"><span data-stu-id="1db06-269">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="1db06-270">Nespravované podpis</span><span class="sxs-lookup"><span data-stu-id="1db06-270">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="1db06-271">Pole v rámci struktury</span><span class="sxs-lookup"><span data-stu-id="1db06-271">Arrays within Structures</span></span>  
 <span data-ttu-id="1db06-272">Nespravované struktury může obsahovat vložené pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-272">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="1db06-273">Ve výchozím nastavení tato vložená pole jsou zařazené jako SAFEARRAY.</span><span class="sxs-lookup"><span data-stu-id="1db06-273">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="1db06-274">V následujícím příkladu `s1` je vložená pole, které je přidělen přímo v rámci struktury sám sebe.</span><span class="sxs-lookup"><span data-stu-id="1db06-274">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="1db06-275">Nespravované reprezentace</span><span class="sxs-lookup"><span data-stu-id="1db06-275">Unmanaged representation</span></span>  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="1db06-276">Pole můžou být zařazené jako <xref:System.Runtime.InteropServices.UnmanagedType>, který vyžaduje, abyste nastavili <xref:System.Runtime.InteropServices.MarshalAsAttribute> pole.</span><span class="sxs-lookup"><span data-stu-id="1db06-276">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="1db06-277">Velikost lze nastavit pouze jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="1db06-277">The size can be set only as a constant.</span></span> <span data-ttu-id="1db06-278">Následující kód ukazuje odpovídající spravované definice `MyStruct`.</span><span class="sxs-lookup"><span data-stu-id="1db06-278">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1db06-279">Viz také</span><span class="sxs-lookup"><span data-stu-id="1db06-279">See Also</span></span>  
 [<span data-ttu-id="1db06-280">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="1db06-280">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)  
 [<span data-ttu-id="1db06-281">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="1db06-281">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)  
 <span data-ttu-id="1db06-282">[Směrovou atributy](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1db06-282">[Directional Attributes](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span></span>  
 [<span data-ttu-id="1db06-283">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="1db06-283">Copying and Pinning</span></span>](copying-and-pinning.md)
