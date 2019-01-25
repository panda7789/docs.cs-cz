---
title: Výchozí chování zařazování
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 587ae32c27a3c779f5f2e4f27bf521e2ca557106
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688997"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="12ee3-102">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="12ee3-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="12ee3-103">Zařazování spolupráce funguje v pravidlech této diktování chování data související s parametry metody během mezi spravovanými a nespravovanými paměti.</span><span class="sxs-lookup"><span data-stu-id="12ee3-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="12ee3-104">Tato integrovaná pravidla takové zařazování aktivity jako typ transformace dat, řízení, zda volaný můžete změnit data předaná do ní a tyto změny vrátit volající a pod kterým okolností, aby zařazování odvozovalo poskytuje optimalizace výkonu.</span><span class="sxs-lookup"><span data-stu-id="12ee3-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="12ee3-105">Tato část popisuje výchozí chování vlastnosti zprostředkovatele komunikace s objekty zařazování služby.</span><span class="sxs-lookup"><span data-stu-id="12ee3-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="12ee3-106">Představuje podrobné informace o zařazování polí, logické typy, typy char, delegátů, tříd, objektů, řetězce a struktury.</span><span class="sxs-lookup"><span data-stu-id="12ee3-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12ee3-107">Zařazování obecných typů není podporováno.</span><span class="sxs-lookup"><span data-stu-id="12ee3-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="12ee3-108">Další informace najdete v tématu [spolupráce pomocí obecných typů](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="12ee3-108">For more information see, [Interoperating Using Generic Types](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="12ee3-109">Správa paměti zařazovacím modulem spolupráce</span><span class="sxs-lookup"><span data-stu-id="12ee3-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="12ee3-110">Interoperační zařazovač se vždy pokusí uvolnit paměť přidělaná nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="12ee3-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="12ee3-111">Toto chování v souladu s pravidly správy paměti modelu COM, ale liší se od pravidel, kterými se řídí nativní kód C++.</span><span class="sxs-lookup"><span data-stu-id="12ee3-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="12ee3-112">Pokud očekáváte, že nativní chování jazyka C++ (žádná uvolnění paměti) může dojít k záměně při používání platformy vyvolat, který automaticky uvolní paměť pro ukazatele.</span><span class="sxs-lookup"><span data-stu-id="12ee3-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="12ee3-113">Například volání následující nespravované metody z knihovny DLL C++ neuvolní automaticky paměti.</span><span class="sxs-lookup"><span data-stu-id="12ee3-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="12ee3-114">Nespravovanému podpisu</span><span class="sxs-lookup"><span data-stu-id="12ee3-114">Unmanaged signature</span></span>  
  
```  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="12ee3-115">Nicméně pokud definujete metodu jako prototyp vyvolání platformy, nahraďte, každé **BSTR** typ s <xref:System.String> zadejte a volat `MethodOne`, modul common language runtime pokusí uvolnit `b` dvakrát.</span><span class="sxs-lookup"><span data-stu-id="12ee3-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="12ee3-116">Můžete změnit chování zařazování pomocí <xref:System.IntPtr> typy spíše než **řetězec** typy.</span><span class="sxs-lookup"><span data-stu-id="12ee3-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="12ee3-117">Vždy používá modul runtime **CoTaskMemFree** metodu pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="12ee3-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="12ee3-118">Pokud nebyla přidělena paměť pracujete s **CoTaskMemAlloc** metoda, je nutné použít **IntPtr** a uvolňují paměť ručně pomocí odpovídající metodu.</span><span class="sxs-lookup"><span data-stu-id="12ee3-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="12ee3-119">Podobně můžete vyhnout automatické paměti uvolnění v situacích, kde by nikdy být uvolnit paměť, například jako při použití **GetCommandLine** funkce ze souboru Kernel32.dll, které vrací ukazatel na paměť jádra.</span><span class="sxs-lookup"><span data-stu-id="12ee3-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="12ee3-120">Podrobnosti o ručně uvolnění paměti, najdete v článku [vyrovnávací paměti – ukázka](https://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="12ee3-120">For details on manually freeing memory, see the [Buffers Sample](https://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="12ee3-121">Výchozí zařazování pro třídy</span><span class="sxs-lookup"><span data-stu-id="12ee3-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="12ee3-122">Třídy lze zařadit pouze pomocí zprostředkovatele komunikace s objekty COM a jsou vždy zařadit jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="12ee3-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="12ee3-123">V některých případech rozhraní použitý k zařazování třídy se nazývá třídy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="12ee3-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="12ee3-124">Informace o přepsání rozhraní třídy s rozhraním podle vašeho výběru, najdete v části [představení rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="12ee3-124">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="12ee3-125">Předání třídy modelu COM</span><span class="sxs-lookup"><span data-stu-id="12ee3-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="12ee3-126">Pokud spravované třídy je předán do modelu COM, interoperační zařazovač automaticky zabalí třídy pomocí serveru proxy modelu COM a předává třídu rozhraní vytvořené metodou proxy k volání metody COM.</span><span class="sxs-lookup"><span data-stu-id="12ee3-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="12ee3-127">Proxy server potom postoupí všechna volání rozhraní třídy zpět do spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="12ee3-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="12ee3-128">Proxy server také poskytuje jiného rozhraní, které nejsou explicitně implementováno třídou.</span><span class="sxs-lookup"><span data-stu-id="12ee3-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="12ee3-129">Proxy server automaticky implementuje rozhraní, jako například **IUnknown** a **IDispatch** jménem třídy.</span><span class="sxs-lookup"><span data-stu-id="12ee3-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="12ee3-130">Předávání tříd pro kód .NET</span><span class="sxs-lookup"><span data-stu-id="12ee3-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="12ee3-131">Třídy typu coclass nejsou obvykle používají jako argumenty metody v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="12ee3-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="12ee3-132">Místo toho výchozí rozhraní se obvykle předává místo coclass.</span><span class="sxs-lookup"><span data-stu-id="12ee3-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="12ee3-133">Rozhraní je předána do spravovaného kódu, interoperační zařazovač zodpovídá za obtékání rozhraní s obálkou správné a předání obálku spravované metody.</span><span class="sxs-lookup"><span data-stu-id="12ee3-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="12ee3-134">Určení, které obálky použití může být obtížné.</span><span class="sxs-lookup"><span data-stu-id="12ee3-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="12ee3-135">Každá instance objektu COM má jeden, jedinečné obálku, bez ohledu na to, kolik rozhraní implementuje objekt.</span><span class="sxs-lookup"><span data-stu-id="12ee3-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="12ee3-136">Například jeden objekt modelu COM, který implementuje rozhraní pět různých má pouze jeden obálky.</span><span class="sxs-lookup"><span data-stu-id="12ee3-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="12ee3-137">Zpřístupňuje stejné obálky všech pět rozhraní.</span><span class="sxs-lookup"><span data-stu-id="12ee3-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="12ee3-138">Pokud se vytvoří dvě instance objektu COM, jsou vytvořeny dva výskyty obálku.</span><span class="sxs-lookup"><span data-stu-id="12ee3-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="12ee3-139">Pro obálku zachovat stejný typ v průběhu svého životního cyklu interoperační zařazovač musí zjistit správné obálky, při prvním rozhraní vystavené objektu předána zařazování.</span><span class="sxs-lookup"><span data-stu-id="12ee3-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="12ee3-140">Aby zařazování odvozovalo identifikuje objekt podle jednoho z rozhraní, které implementuje objekt.</span><span class="sxs-lookup"><span data-stu-id="12ee3-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="12ee3-141">V následujícím příkladu, aby zařazování odvozovalo Určuje, že by měl být obálkové třídy slouží k zabalení rozhraní, které bylo předáno do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="12ee3-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="12ee3-142">Při zařazování se nejprve předává rozhraní, aby zařazování odvozovalo kontroluje, zda rozhraní pochází ze známého objektu.</span><span class="sxs-lookup"><span data-stu-id="12ee3-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="12ee3-143">Tato kontrola probíhá ve dvou situacích:</span><span class="sxs-lookup"><span data-stu-id="12ee3-143">This check occurs in two situations:</span></span>  
  
-   <span data-ttu-id="12ee3-144">Rozhraní je prováděna jiný spravovaný objekt, který byl předán COM jinde.</span><span class="sxs-lookup"><span data-stu-id="12ee3-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="12ee3-145">Zařazování mohli snadno identifikovat rozhraní vystavené spravovaných objektů a bude schopen odpovídat rozhraní s spravovaný objekt, který poskytuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="12ee3-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="12ee3-146">Spravovaný objekt je pak předán do metody a je zapotřebí žádné obálky.</span><span class="sxs-lookup"><span data-stu-id="12ee3-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
-   <span data-ttu-id="12ee3-147">Objekt, který už je zabalená implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="12ee3-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="12ee3-148">Pokud chcete zjistit, zda se jedná o tento případ, aby zařazování odvozovalo dotaz se týká objektu pro jeho **IUnknown** rozhraní a porovnává rozhraní vrácená rozhraním jiné objekty, které už jsou zabaleny.</span><span class="sxs-lookup"><span data-stu-id="12ee3-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="12ee3-149">Pokud rozhraní je stejný jako u jiného obálky, objekty mají stejnou identitu a existující obálky je předán metodě.</span><span class="sxs-lookup"><span data-stu-id="12ee3-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="12ee3-150">Pokud rozhraní není od známých objektu, aby zařazování odvozovalo provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="12ee3-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1.  <span data-ttu-id="12ee3-151">Aby zařazování odvozovalo dotaz se týká objektu pro **IProvideClassInfo2** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="12ee3-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="12ee3-152">Pokud je zadán, aby zařazování odvozovalo používá CLSID vrácená z **IProvideClassInfo2.GetGUID** k identifikaci coclass poskytuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="12ee3-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="12ee3-153">S identifikátorem CLSID aby zařazování odvozovalo najdou obálky z registru Pokud sestavení byl dříve zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="12ee3-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2.  <span data-ttu-id="12ee3-154">Aby zařazování odvozovalo dotazuje rozhraní pro **iprovideclassinfo –** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="12ee3-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="12ee3-155">Pokud je zadán, aby zařazování odvozovalo používá **ITypeInfo** vrácená **IProvideClassInfo.GetClassinfo** určit identifikátor CLSID třídy vystavení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="12ee3-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="12ee3-156">Zařazování lze použít k vyhledání metadat pro obálku identifikátor CLSID.</span><span class="sxs-lookup"><span data-stu-id="12ee3-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3.  <span data-ttu-id="12ee3-157">Pokud stále zařazování nemůže určovat třídu, zabalí rozhraní s obecný Obálkový třídu s názvem **System.__ComObject**.</span><span class="sxs-lookup"><span data-stu-id="12ee3-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="12ee3-158">Výchozí zařazování pro delegáty</span><span class="sxs-lookup"><span data-stu-id="12ee3-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="12ee3-159">Spravované delegáta je zařadit jako rozhraní modelu COM nebo jako ukazatel na funkci, na základě mechanismu volání:</span><span class="sxs-lookup"><span data-stu-id="12ee3-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
-   <span data-ttu-id="12ee3-160">Pro platformu vyvolání, delegát je zařadit jako ukazatele nespravované funkce ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="12ee3-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
-   <span data-ttu-id="12ee3-161">Pro komunikace s objekty COM, delegát zařadit jako rozhraní modelu COM typu **_Delegate** ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="12ee3-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="12ee3-162">**_Delegate** rozhraní je definovaný v knihovně typů Mscorlib.tlb a obsahuje <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> metodu, která umožňuje volat metodu, která odkazuje na delegáta.</span><span class="sxs-lookup"><span data-stu-id="12ee3-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="12ee3-163">V následující tabulce jsou uvedeny zařazování možnosti pro datový typ spravovaného delegáta.</span><span class="sxs-lookup"><span data-stu-id="12ee3-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="12ee3-164"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> zařazování delegátů hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="12ee3-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="12ee3-165">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="12ee3-165">Enumeration type</span></span>|<span data-ttu-id="12ee3-166">Popis nespravované formátu</span><span class="sxs-lookup"><span data-stu-id="12ee3-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="12ee3-167">**UnmanagedType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="12ee3-167">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="12ee3-168">Ukazatel nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="12ee3-168">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="12ee3-169">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="12ee3-169">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="12ee3-170">Rozhraní typu **_Delegate**, jak jsou definovány v knihovnu Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="12ee3-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="12ee3-171">Zvažte následující příklad kódu, ve kterém metody `DelegateTestInterface` jsou exportovány do knihovny typů modelu COM.</span><span class="sxs-lookup"><span data-stu-id="12ee3-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="12ee3-172">Všimněte si, že pouze deleguje označené **ref** (nebo **ByRef**) – klíčové slovo jsou předány jako vstup a výstup parametry.</span><span class="sxs-lookup"><span data-stu-id="12ee3-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public interface DelegateTest {  
void m1(Delegate d);  
void m2([MarshalAs(UnmanagedType.Interface)] Delegate d);     
void m3([MarshalAs(UnmanagedType.Interface)] ref Delegate d);    
void m4([MarshalAs(UnmanagedType.FunctionPtr)] Delegate d);   
void m5([MarshalAs(UnmanagedType.FunctionPtr)] ref Delegate d);     
}  
```  
  
### <a name="type-library-representation"></a><span data-ttu-id="12ee3-173">Knihovna reprezentaci typu</span><span class="sxs-lookup"><span data-stu-id="12ee3-173">Type library representation</span></span>  
  
```  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 <span data-ttu-id="12ee3-174">Ukazatel na funkci může být dereferencován, stejně jako může být dereferencován druhý ukazatel nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="12ee3-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="12ee3-175">V tomto příkladu, pokud dva delegáty, které jsou zařazeny jako <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, výsledek je `int` a ukazatel `int`.</span><span class="sxs-lookup"><span data-stu-id="12ee3-175">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="12ee3-176">Protože se právě zařazovat typy delegátů, `int` zde představuje ukazatel na typu void (`void*`), což je adresa delegáta v paměti.</span><span class="sxs-lookup"><span data-stu-id="12ee3-176">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="12ee3-177">Jinými slovy, tento výsledek je specifická pro 32bitové systémy Windows, v od té doby `int` zde představuje velikost ukazatele funkce.</span><span class="sxs-lookup"><span data-stu-id="12ee3-177">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
>  <span data-ttu-id="12ee3-178">Odkaz na ukazatel funkce na spravované delegáta drží nespravovaný kód nezabrání modul common language runtime v provádění uvolnění paměti na spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="12ee3-178">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="12ee3-179">Například následující kód je nesprávný protože odkaz na `cb` objekt předaný `SetChangeHandler` metody neudržuje `cb` aktivní za dobu životnosti `Test` – metoda.</span><span class="sxs-lookup"><span data-stu-id="12ee3-179">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="12ee3-180">Jednou `cb` vynuceno uvolnění paměti je objekt, předán ukazatel funkce `SetChangeHandler` již není platný.</span><span class="sxs-lookup"><span data-stu-id="12ee3-180">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
```csharp  
public class ExternalAPI {  
   [DllImport("External.dll")]  
   public static extern void SetChangeHandler(  
      [MarshalAs(UnmanagedType.FunctionPtr)]ChangeDelegate d);  
}  
public delegate bool ChangeDelegate([MarshalAs(UnmanagedType.LPWStr) string S);  
public class CallBackClass {  
   public bool OnChange(string S){ return true;}  
}  
internal class DelegateTest {  
   public static void Test() {  
      CallBackClass cb = new CallBackClass();  
      // Caution: The following reference on the cb object does not keep the   
      // object from being garbage collected after the Main method   
      // executes.  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));     
   }  
}  
```  
  
 <span data-ttu-id="12ee3-181">Pro kompenzaci neočekávané uvolňování paměti, volající musíte zajistit, aby `cb` objektu, zůstane aktivní, dokud se ukazatel Nespravované funkce používá.</span><span class="sxs-lookup"><span data-stu-id="12ee3-181">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="12ee3-182">Volitelně můžete mít nespravovaný kód upozornit spravovaného kódu na ukazatel funkce už je nepotřebujete, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="12ee3-182">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
```csharp  
internal class DelegateTest {  
   CallBackClass cb;  
   // Called before ever using the callback function.  
   public static void SetChangeHandler() {  
      cb = new CallBackClass();  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));  
   }  
   // Called after using the callback function for the last time.  
   public static void RemoveChangeHandler() {  
      // The cb object can be collected now. The unmanaged code is   
      // finished with the callback function.  
      cb = null;  
   }  
}  
```  
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="12ee3-183">Výchozí zařazování pro typy hodnot</span><span class="sxs-lookup"><span data-stu-id="12ee3-183">Default marshaling for value types</span></span>  
 <span data-ttu-id="12ee3-184">Většina typy hodnot, jako jsou celá čísla a čísla s plovoucí desetinnou čárkou, jsou [blittable](blittable-and-non-blittable-types.md) a nevyžadují, aby zařazování.</span><span class="sxs-lookup"><span data-stu-id="12ee3-184">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="12ee3-185">Další [nepřenositelné](blittable-and-non-blittable-types.md) typy mají odlišné reprezentace v spravované a nespravované paměti a nevyžadují zařazování.</span><span class="sxs-lookup"><span data-stu-id="12ee3-185">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="12ee3-186">Jiné typy stále vyžadují explicitní formátování napříč hranicemi.</span><span class="sxs-lookup"><span data-stu-id="12ee3-186">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="12ee3-187">Toto téma obsahuje informace použijte pro typy formátovaná hodnota:</span><span class="sxs-lookup"><span data-stu-id="12ee3-187">This topic provides the follow information on formatted value types:</span></span>  
  
-   [<span data-ttu-id="12ee3-188">Typy hodnot používá v platformě vyvolání</span><span class="sxs-lookup"><span data-stu-id="12ee3-188">Value Types Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforvaluetypesanchor2)  
  
-   [<span data-ttu-id="12ee3-189">Typy hodnot používá ve spolupráci s COM</span><span class="sxs-lookup"><span data-stu-id="12ee3-189">Value Types Used in COM Interop</span></span>](#cpcondefaultmarshalingforvaluetypesanchor3)  
  
 <span data-ttu-id="12ee3-190">Kromě popisující typy formátovaný, toto téma popisuje [systém hodnotou typy](#cpcondefaultmarshalingforvaluetypesanchor1) , které mají neobvyklé chování zařazování.</span><span class="sxs-lookup"><span data-stu-id="12ee3-190">In addition to describing formatted types, this topic identifies [System Value Types](#cpcondefaultmarshalingforvaluetypesanchor1) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="12ee3-191">Formátovaný typ je komplexní typ, který obsahuje informace, které explicitně určuje rozložení z jejích členů v paměti.</span><span class="sxs-lookup"><span data-stu-id="12ee3-191">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="12ee3-192">Informace o rozložení člen je prováděno pomocí <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="12ee3-192">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="12ee3-193">Rozložení může být jedna z následujících <xref:System.Runtime.InteropServices.LayoutKind> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="12ee3-193">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
-   <span data-ttu-id="12ee3-194">**LayoutKind.Automatic**</span><span class="sxs-lookup"><span data-stu-id="12ee3-194">**LayoutKind.Automatic**</span></span>  
  
     <span data-ttu-id="12ee3-195">Označuje, že je modul common language runtime můžete změnit pořadí členů typu efektivitu.</span><span class="sxs-lookup"><span data-stu-id="12ee3-195">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="12ee3-196">Pokud typ hodnoty je předán do nespravovaného kódu, rozložení členy ale předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="12ee3-196">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="12ee3-197">Pokus o zařazení takovouto strukturu automaticky dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="12ee3-197">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
-   <span data-ttu-id="12ee3-198">**LayoutKind.Sequential**</span><span class="sxs-lookup"><span data-stu-id="12ee3-198">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="12ee3-199">Označuje, že členy typu rozloží v nespravované paměti ve stejném pořadí, v jakém jsou uvedeny v definici spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="12ee3-199">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
-   <span data-ttu-id="12ee3-200">**LayoutKind.Explicit**</span><span class="sxs-lookup"><span data-stu-id="12ee3-200">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="12ee3-201">Označuje, že členové jsou rozloženy podle <xref:System.Runtime.InteropServices.FieldOffsetAttribute> součástí každé pole.</span><span class="sxs-lookup"><span data-stu-id="12ee3-201">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor2"></a>   
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="12ee3-202">Typy hodnot používá v platformě vyvolání</span><span class="sxs-lookup"><span data-stu-id="12ee3-202">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="12ee3-203">V následujícím příkladu `Point` a `Rect` typy poskytují člen informace o rozložení pomocí **StructLayoutAttribute –**.</span><span class="sxs-lookup"><span data-stu-id="12ee3-203">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
   Public x As Integer  
   Public y As Integer  
End Structure  
<StructLayout(LayoutKind.Explicit)> Public Structure Rect  
   <FieldOffset(0)> Public left As Integer  
   <FieldOffset(4)> Public top As Integer  
   <FieldOffset(8)> Public right As Integer  
   <FieldOffset(12)> Public bottom As Integer  
End Structure  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
   public int x;  
   public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
   [FieldOffset(0)] public int left;  
   [FieldOffset(4)] public int top;  
   [FieldOffset(8)] public int right;  
   [FieldOffset(12)] public int bottom;  
}  
```  
  
 <span data-ttu-id="12ee3-204">Při zařazení na nespravovaný kód, jsou tyto typy formátovaný zařadit jako struktury C-style.</span><span class="sxs-lookup"><span data-stu-id="12ee3-204">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="12ee3-205">To poskytuje snadný způsob volání nespravovaného rozhraní API, která má strukturu argumenty.</span><span class="sxs-lookup"><span data-stu-id="12ee3-205">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="12ee3-206">Například `POINT` a `RECT` struktury může být předán rozhraní Microsoft Win32 API **PtInRect** funkce takto:</span><span class="sxs-lookup"><span data-stu-id="12ee3-206">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Win32 API **PtInRect** function as follows:</span></span>  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="12ee3-207">Můžete předat struktury použití následující platformy vyvolat definice:</span><span class="sxs-lookup"><span data-stu-id="12ee3-207">You can pass structures using the following platform invoke definition:</span></span>  
  
```vb  
Class Win32API      
   Declare Auto Function PtInRect Lib "User32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("User32.dll")]  
   public static extern Bool PtInRect(ref Rect r, Point p);  
}  
```  
  
 <span data-ttu-id="12ee3-208">`Rect` Hodnotový typ musí být předány podle odkazu, protože nespravované rozhraní API očekává ukazatel `RECT` má být předán funkci.</span><span class="sxs-lookup"><span data-stu-id="12ee3-208">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="12ee3-209">`Point` Typ hodnoty je předán podle hodnoty, protože nespravované rozhraní API očekává, že `POINT` mají být předány do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="12ee3-209">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="12ee3-210">Tento malý rozdíl je velmi důležité.</span><span class="sxs-lookup"><span data-stu-id="12ee3-210">This subtle difference is very important.</span></span> <span data-ttu-id="12ee3-211">Odkazy jsou předány do nespravovaného kódu jako ukazatele.</span><span class="sxs-lookup"><span data-stu-id="12ee3-211">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="12ee3-212">Hodnoty jsou předány na nespravovaný kód v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="12ee3-212">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12ee3-213">Když formátovaný typ je zařazen jako strukturu, jsou přístupné pouze na pole v rámci typu.</span><span class="sxs-lookup"><span data-stu-id="12ee3-213">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="12ee3-214">Pokud má typ metody, vlastnosti nebo události, je přístupný z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="12ee3-214">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="12ee3-215">Třídy mohou také být zařazení na nespravovaný kód jako struktury stylu C, pokud došlo k nápravě rozložení.</span><span class="sxs-lookup"><span data-stu-id="12ee3-215">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="12ee3-216">Informace o rozložení člen třídy je také součástí <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="12ee3-216">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="12ee3-217">Hlavní rozdíl mezi typy hodnot s pevně rozložení a třídy s pevným rozložením je způsob, ve kterém jsou zařazení na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="12ee3-217">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="12ee3-218">Typy hodnot jsou předávány hodnotou (v zásobníku), a proto neuvidí všechny změny provedené členy typu volaným volajícím.</span><span class="sxs-lookup"><span data-stu-id="12ee3-218">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="12ee3-219">Typy odkazů jsou předány podle odkazu (odkaz na typ je předány do zásobníku); v důsledku toho se zobrazují všechny změny provedené na členy typu typu blittable volaným volajícím.</span><span class="sxs-lookup"><span data-stu-id="12ee3-219">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12ee3-220">Pokud je odkazový typ členy nepřenositelné typy, je vyžadován převod dvakrát: poprvé, když je argument předaný do nespravované oblasti a druhý čas při návratu z volání.</span><span class="sxs-lookup"><span data-stu-id="12ee3-220">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="12ee3-221">Kvůli tomu nároky parametry In nebo Out musí explicitně použít pro argument Pokud volající požaduje zobrazíte změny volaným.</span><span class="sxs-lookup"><span data-stu-id="12ee3-221">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="12ee3-222">V následujícím příkladu `SystemTime` třída má sekvenční rozložení a mohou být předány do rozhraní API systému Win32 **GetSystemTime** funkce.</span><span class="sxs-lookup"><span data-stu-id="12ee3-222">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Win32 API **GetSystemTime** function.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class SystemTime  
   Public wYear As System.UInt16  
   Public wMonth As System.UInt16  
   Public wDayOfWeek As System.UInt16  
   Public wDay As System.UInt16  
   Public wHour As System.UInt16  
   Public wMinute As System.UInt16  
   Public wSecond As System.UInt16  
   Public wMilliseconds As System.UInt16  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
   public class SystemTime {  
   public ushort wYear;   
   public ushort wMonth;  
   public ushort wDayOfWeek;   
   public ushort wDay;   
   public ushort wHour;   
   public ushort wMinute;   
   public ushort wSecond;   
   public ushort wMilliseconds;   
}  
```  
  
 <span data-ttu-id="12ee3-223">**GetSystemTime** funkce je definována takto:</span><span class="sxs-lookup"><span data-stu-id="12ee3-223">The **GetSystemTime** function is defined as follows:</span></span>  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="12ee3-224">Definice pro vyvolání ekvivalentní platformy **GetSystemTime** vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="12ee3-224">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
```vb  
Public Class Win32  
   Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (ByVal sysTime _  
   As SystemTime)  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("Kernel32.dll", CharSet=CharSet.Auto)]  
   public static extern void GetSystemTime(SystemTime st);  
}  
```  
  
 <span data-ttu-id="12ee3-225">Všimněte si, že `SystemTime` argument není zadána jako argument typu odkaz, protože `SystemTime` je třída, nikoli typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="12ee3-225">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="12ee3-226">Na rozdíl od typy hodnot jsou vždy třídy předány podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="12ee3-226">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="12ee3-227">Následující příklad kódu ukazuje jiné `Point` třídu, která obsahuje metodu nazvanou `SetXY`.</span><span class="sxs-lookup"><span data-stu-id="12ee3-227">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="12ee3-228">Protože tento typ nemá sekvenční rozložení, může být předán nespravovanému kódu a zařadit jako struktury.</span><span class="sxs-lookup"><span data-stu-id="12ee3-228">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="12ee3-229">Ale `SetXY` člen se nedá volat z nespravovaného kódu i v případě, že objekt je předán odkazem.</span><span class="sxs-lookup"><span data-stu-id="12ee3-229">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class Point  
   Private x, y As Integer  
   Public Sub SetXY(x As Integer, y As Integer)  
      Me.x = x  
      Me.y = y  
   End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class Point {  
   int x, y;  
   public void SetXY(int x, int y){   
      this.x = x;  
      this.y = y;  
   }  
}  
```  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor3"></a>   
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="12ee3-230">Typy hodnot používá ve spolupráci s COM</span><span class="sxs-lookup"><span data-stu-id="12ee3-230">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="12ee3-231">Volání metody vzájemné spolupráce COM může být předán také formátovaný typy.</span><span class="sxs-lookup"><span data-stu-id="12ee3-231">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="12ee3-232">Ve skutečnosti při exportu do knihovny typů, typů hodnot se automaticky převedou na struktury.</span><span class="sxs-lookup"><span data-stu-id="12ee3-232">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="12ee3-233">Jak ukazuje následující příklad `Point` typ hodnoty změní typ definice (typedef) s názvem `Point`.</span><span class="sxs-lookup"><span data-stu-id="12ee3-233">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="12ee3-234">Všude, kde `Point` jsou nahrazeny typ hodnoty jinde v knihovně typů `Point` typedef.</span><span class="sxs-lookup"><span data-stu-id="12ee3-234">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="12ee3-235">**Knihovna reprezentaci typu**</span><span class="sxs-lookup"><span data-stu-id="12ee3-235">**Type library representation**</span></span>  
  
```  
typedef struct tagPoint {  
   int x;  
   int y;  
} Point;  
interface _Graphics {  
   …  
   HRESULT SetPoint ([in] Point p)  
   HRESULT SetPointRef ([in,out] Point *p)  
   HRESULT GetPoint ([out,retval] Point *p)  
}  
```  
  
 <span data-ttu-id="12ee3-236">Stejná pravidla použitý k zařazování hodnoty a odkazy na platformu vyvolání volání se používají při zařazování prostřednictvím rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="12ee3-236">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="12ee3-237">Například, pokud instance `Point` z rozhraní .NET Framework do modelu COM, je předán typ hodnoty `Point` je předán podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="12ee3-237">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="12ee3-238">Pokud `Point` typ hodnoty je předána odkazem, ukazatel `Point` předány v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="12ee3-238">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="12ee3-239">Interoperační zařazovač nepodporuje vyšší úrovní dereference (**bodu** \* \*) v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="12ee3-239">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="12ee3-240">Struktury s <xref:System.Runtime.InteropServices.LayoutKind> nastavena na hodnotu výčtu **explicitní** nelze použít ve spolupráci s COM, protože exportované knihovny typů nemůže express s explicitním rozložením.</span><span class="sxs-lookup"><span data-stu-id="12ee3-240">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor1"></a>   
### <a name="system-value-types"></a><span data-ttu-id="12ee3-241">Systém typů hodnot</span><span class="sxs-lookup"><span data-stu-id="12ee3-241">System Value Types</span></span>  
 <span data-ttu-id="12ee3-242"><xref:System> Obor názvů má několik typy hodnot, které představují v podobě boxed primitivních typů modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="12ee3-242">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="12ee3-243">Například typ hodnoty <xref:System.Int32?displayProperty=nameWithType> struktura představuje v podobě boxed z **ELEMENT_TYPE_I4**.</span><span class="sxs-lookup"><span data-stu-id="12ee3-243">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="12ee3-244">Místo zařazování typů jako struktury, jako ostatní typy formátovaný můžete přeuspořádat je stejným způsobem jako primitivní typy, které jsou pole.</span><span class="sxs-lookup"><span data-stu-id="12ee3-244">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="12ee3-245">**System.Int32** proto zařazena jako **ELEMENT_TYPE_I4** místo jako struktura obsahující jednoho člena typu **dlouhé**.</span><span class="sxs-lookup"><span data-stu-id="12ee3-245">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="12ee3-246">Následující tabulka obsahuje seznam typů hodnot v **systému** obor názvů, který jsou zabalené reprezentace primitivní typy.</span><span class="sxs-lookup"><span data-stu-id="12ee3-246">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="12ee3-247">Typ hodnoty systému</span><span class="sxs-lookup"><span data-stu-id="12ee3-247">System value type</span></span>|<span data-ttu-id="12ee3-248">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="12ee3-248">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="12ee3-249">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="12ee3-249">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="12ee3-250">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="12ee3-250">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="12ee3-251">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="12ee3-251">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="12ee3-252">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="12ee3-252">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="12ee3-253">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="12ee3-253">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="12ee3-254">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="12ee3-254">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="12ee3-255">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="12ee3-255">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="12ee3-256">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="12ee3-256">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="12ee3-257">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="12ee3-257">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="12ee3-258">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="12ee3-258">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="12ee3-259">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="12ee3-259">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="12ee3-260">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="12ee3-260">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="12ee3-261">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="12ee3-261">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="12ee3-262">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="12ee3-262">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="12ee3-263">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="12ee3-263">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="12ee3-264">Některé hodnoty typů v **systému** obor názvů jsou zpracovány jinak.</span><span class="sxs-lookup"><span data-stu-id="12ee3-264">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="12ee3-265">Protože nespravovaný kód už má zavedené formáty pro tyto typy, aby zařazování odvozovalo má zvláštní pravidla pro zařazování je.</span><span class="sxs-lookup"><span data-stu-id="12ee3-265">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="12ee3-266">Následující tabulka uvádí typy zvláštní hodnota v **systému** obor názvů, a také jsou zařazeny do nespravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="12ee3-266">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="12ee3-267">Typ hodnoty systému</span><span class="sxs-lookup"><span data-stu-id="12ee3-267">System value type</span></span>|<span data-ttu-id="12ee3-268">IDL – typ</span><span class="sxs-lookup"><span data-stu-id="12ee3-268">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="12ee3-269">**DATUM**</span><span class="sxs-lookup"><span data-stu-id="12ee3-269">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="12ee3-270">**DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="12ee3-270">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="12ee3-271">**GUID**</span><span class="sxs-lookup"><span data-stu-id="12ee3-271">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="12ee3-272">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="12ee3-272">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="12ee3-273">Následující kód znázorňuje definici nespravovaných typů **datum**, **GUID**, **DESÍTKOVÉ**, a **OLE_COLOR** Stdole2 typu Knihovna.</span><span class="sxs-lookup"><span data-stu-id="12ee3-273">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="12ee3-274">Knihovna reprezentaci typu</span><span class="sxs-lookup"><span data-stu-id="12ee3-274">Type library representation</span></span>  
  
```  
typedef double DATE;  
typedef DWORD OLE_COLOR;  
  
typedef struct tagDEC {  
    USHORT    wReserved;  
    BYTE      scale;  
    BYTE      sign;  
    ULONG     Hi32;  
    ULONGLONG Lo64;  
} DECIMAL;  
  
typedef struct tagGUID {  
    DWORD Data1;  
    WORD  Data2;  
    WORD  Data3;  
    BYTE  Data4[ 8 ];  
} GUID;  
```  
  
 <span data-ttu-id="12ee3-275">Následující kód ukazuje odpovídající definice v spravovanou `IValueTypes` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="12ee3-275">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
```vb  
Public Interface IValueTypes  
   Sub M1(d As System.DateTime)  
   Sub M2(d As System.Guid)  
   Sub M3(d As System.Decimal)  
   Sub M4(d As System.Drawing.Color)  
End Interface  
```  
  
```csharp  
public interface IValueTypes {  
   void M1(System.DateTime d);  
   void M2(System.Guid d);  
   void M3(System.Decimal d);  
   void M4(System.Drawing.Color d);  
}  
```  
  
#### <a name="type-library-representation"></a><span data-ttu-id="12ee3-276">Knihovna reprezentaci typu</span><span class="sxs-lookup"><span data-stu-id="12ee3-276">Type library representation</span></span>  
  
```  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="12ee3-277">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12ee3-277">See also</span></span>
- [<span data-ttu-id="12ee3-278">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="12ee3-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="12ee3-279">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="12ee3-279">Copying and Pinning</span></span>](copying-and-pinning.md)
- [<span data-ttu-id="12ee3-280">Výchozí zařazování pro pole</span><span class="sxs-lookup"><span data-stu-id="12ee3-280">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)
- [<span data-ttu-id="12ee3-281">Výchozí zařazování pro objekty</span><span class="sxs-lookup"><span data-stu-id="12ee3-281">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)
- [<span data-ttu-id="12ee3-282">Výchozí zařazování pro řetězce</span><span class="sxs-lookup"><span data-stu-id="12ee3-282">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
