---
title: "Výchozí chování zařazování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e66caf800fd49b4822ee22326b8a5cf712d99bb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="5b97d-102">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="5b97d-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="5b97d-103">Zařazování spolupráce funguje v pravidlech že tu určují chování data související s parametry metody jak předává mezi spravovanými a nespravovanými paměti.</span><span class="sxs-lookup"><span data-stu-id="5b97d-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="5b97d-104">Tyto vestavěné pravidla řízení takové zařazování aktivitám v podobě transformace typu dat, zda volaný můžete změnit data do ní předán a tyto změny vrátit volajícímu, a pod kterým okolností zařazování poskytuje optimalizace výkonu.</span><span class="sxs-lookup"><span data-stu-id="5b97d-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="5b97d-105">Tato část identifikuje výchozí chování charakteristika zprostředkovatel komunikace s objekty zařazování služby.</span><span class="sxs-lookup"><span data-stu-id="5b97d-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="5b97d-106">Představuje podrobné informace o zařazování polí, logická hodnota typy, typy char, delegáti, tříd, objekty, řetězce a struktury.</span><span class="sxs-lookup"><span data-stu-id="5b97d-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b97d-107">Zařazování obecných typů není podporována.</span><span class="sxs-lookup"><span data-stu-id="5b97d-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="5b97d-108">Další informace najdete v tématu [spolupráce pomocí obecných typů](http://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58).</span><span class="sxs-lookup"><span data-stu-id="5b97d-108">For more information see, [Interoperating Using Generic Types](http://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="5b97d-109">Správa paměti s spolupráce zařazování vláken</span><span class="sxs-lookup"><span data-stu-id="5b97d-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="5b97d-110">Zařazování spolupráce se vždy pokusí volné paměti přidělené nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5b97d-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="5b97d-111">Toto chování je v souladu s COM pravidla správy paměti, ale se liší od pravidla, která řídí nativní C++.</span><span class="sxs-lookup"><span data-stu-id="5b97d-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="5b97d-112">Pokud očekáváte, že nativní chování C++ (bez uvolnění paměti) může dojít k záměně při použití platformy vyvolání, které automaticky uvolní paměť pro ukazatele.</span><span class="sxs-lookup"><span data-stu-id="5b97d-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="5b97d-113">Například volání následující nespravovanou metodu z knihovny DLL C++ neuvolní automaticky libovolná paměť.</span><span class="sxs-lookup"><span data-stu-id="5b97d-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="5b97d-114">Nespravované podpis</span><span class="sxs-lookup"><span data-stu-id="5b97d-114">Unmanaged signature</span></span>  
  
```  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="5b97d-115">Ale pokud definujete metodu jako vyvolání prototypu platformy, nahraďte, každý **BSTR** zadejte s <xref:System.String> zadejte a volání `MethodOne`, modul se pokusí volné `b` dvakrát.</span><span class="sxs-lookup"><span data-stu-id="5b97d-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="5b97d-116">Chování zařazování můžete změnit pomocí <xref:System.IntPtr> typy místo **řetězec** typy.</span><span class="sxs-lookup"><span data-stu-id="5b97d-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="5b97d-117">Modul runtime vždy používá **CoTaskMemFree** metodu pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="5b97d-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="5b97d-118">Pokud nebyl přiřazen paměti, že pracujete s **CoTaskMemAlloc** metodu, musíte použít **IntPtr** a volné paměti ručně pomocí odpovídající metodu.</span><span class="sxs-lookup"><span data-stu-id="5b97d-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="5b97d-119">Podobně se můžete vyhnout automatické paměti uvolňování v situacích, kde by nikdy uvolnit paměť, například jako při použití **GetCommandLine** funkce z Kernel32.dll, který vrací ukazatel na paměti jádra.</span><span class="sxs-lookup"><span data-stu-id="5b97d-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="5b97d-120">Podrobnosti o ručně uvolnění paměti najdete v tématu [vyrovnávací paměti ukázka](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5).</span><span class="sxs-lookup"><span data-stu-id="5b97d-120">For details on manually freeing memory, see the [Buffers Sample](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="5b97d-121">Výchozí zařazování pro třídy</span><span class="sxs-lookup"><span data-stu-id="5b97d-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="5b97d-122">Třídy mohou být zařazena pouze pomocí zprostředkovatele komunikace s objekty COM a jsou vždycky zařazené jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5b97d-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="5b97d-123">V některých případech rozhraní sloužící k zařazování třídy se nazývá rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="5b97d-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="5b97d-124">Informace o přepsání třídy rozhraní s rozhraním zvoleného najdete v tématu [představení rozhraní třídy](http://msdn.microsoft.com/library/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span><span class="sxs-lookup"><span data-stu-id="5b97d-124">For information about overriding the class interface with an interface of your choice, see [Introducing the Class Interface](http://msdn.microsoft.com/library/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="5b97d-125">Předávání tříd do modelu COM</span><span class="sxs-lookup"><span data-stu-id="5b97d-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="5b97d-126">Když spravovanou třídou předána do modelu COM, spolupráce vláken automaticky zabalí třídy pomocí modelu COM serveru proxy a předá rozhraní třída vyprodukované proxy server a volání metody COM.</span><span class="sxs-lookup"><span data-stu-id="5b97d-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="5b97d-127">Proxy server pak deleguje všechna volání na rozhraní třída zpět do spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="5b97d-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="5b97d-128">Proxy server taky zpřístupňuje další rozhraní, která nejsou explicitně implementované v třídě.</span><span class="sxs-lookup"><span data-stu-id="5b97d-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="5b97d-129">Proxy server, jako automaticky implementuje rozhraní **IUnknown** a **IDispatch** jménem třídy.</span><span class="sxs-lookup"><span data-stu-id="5b97d-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="5b97d-130">Předávání tříd pro kód .NET</span><span class="sxs-lookup"><span data-stu-id="5b97d-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="5b97d-131">Třídy typu coclass se obvykle nepoužívá jako argumenty metoda v modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5b97d-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="5b97d-132">Místo toho výchozí rozhraní se obvykle předává místo coclass.</span><span class="sxs-lookup"><span data-stu-id="5b97d-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="5b97d-133">Když rozhraní předána do spravovaného kódu, je zodpovědná za zabalení rozhraní s správné obálku a předání obálku spravované metoda spolupráce vláken.</span><span class="sxs-lookup"><span data-stu-id="5b97d-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="5b97d-134">Určení, které obálka pro použití může být obtížné.</span><span class="sxs-lookup"><span data-stu-id="5b97d-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="5b97d-135">Všechny instance objektu COM má jeden, jedinečné obálku, bez ohledu na to, kolik rozhraní implementuje objekt.</span><span class="sxs-lookup"><span data-stu-id="5b97d-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="5b97d-136">Například jeden objekt COM, který implementuje rozhraní pět různých má jenom jeden obálku.</span><span class="sxs-lookup"><span data-stu-id="5b97d-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="5b97d-137">Stejné obálku zpřístupní všechny pět rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5b97d-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="5b97d-138">Pokud jsou vytvořeny dva instance objektu COM, vytvoří se dvě instance obálku.</span><span class="sxs-lookup"><span data-stu-id="5b97d-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="5b97d-139">Pro obálku zachování stejného typu v průběhu své životnosti musí spolupráce vláken identifikovat správný obálku prvním rozhraní vystavené objektu je předána vláken.</span><span class="sxs-lookup"><span data-stu-id="5b97d-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="5b97d-140">Zařazování identifikuje objekt pohledem na jednu z rozhraní, které implementuje objekt.</span><span class="sxs-lookup"><span data-stu-id="5b97d-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="5b97d-141">Například zařazování Určuje, že obálku třída by měla slouží k zabalení rozhraní, který byl předán do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5b97d-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="5b97d-142">Když rozhraní nejprve předána zařazování, zařazování zkontroluje, zda rozhraní pochází od známých objektu.</span><span class="sxs-lookup"><span data-stu-id="5b97d-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="5b97d-143">Tato kontrola probíhá ve dvou situacích:</span><span class="sxs-lookup"><span data-stu-id="5b97d-143">This check occurs in two situations:</span></span>  
  
-   <span data-ttu-id="5b97d-144">Rozhraní se implementuje jiný spravovaný objekt, který byl předán COM jinde.</span><span class="sxs-lookup"><span data-stu-id="5b97d-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="5b97d-145">Zařazování můžete snadno identifikovat rozhraní vystavené spravované objekty a může tak, aby odpovídaly rozhraní s spravovaný objekt, který poskytuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="5b97d-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="5b97d-146">Spravovaného objektu je předána metodě a je zapotřebí žádné obálku.</span><span class="sxs-lookup"><span data-stu-id="5b97d-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
-   <span data-ttu-id="5b97d-147">Objekt, který už je zabalená je implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5b97d-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="5b97d-148">Pokud chcete zjistit, jestli se jedná o tento případ, dotazuje se vláken objektu pro jeho **IUnknown** rozhraní a porovná rozhraní vrácený rozhraní jiné objekty, které jsou již uzavřen.</span><span class="sxs-lookup"><span data-stu-id="5b97d-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="5b97d-149">Pokud rozhraní je stejný jako u jiného obálky, objekty mají stejnou identitu a existující obálky je předaný metodě.</span><span class="sxs-lookup"><span data-stu-id="5b97d-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="5b97d-150">Pokud není rozhraní z objektu známé, zařazování provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="5b97d-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1.  <span data-ttu-id="5b97d-151">Objekt pro dotazy zařazování vláken **IProvideClassInfo2** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5b97d-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="5b97d-152">Pokud je zadán, zařazování používá CLSID vrácená z **IProvideClassInfo2.GetGUID** k identifikaci třída typu coclass poskytuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5b97d-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="5b97d-153">S CLSID najdou zařazování obálku z registru, pokud sestavení již byla zaregistrována.</span><span class="sxs-lookup"><span data-stu-id="5b97d-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2.  <span data-ttu-id="5b97d-154">Rozhraní pro dotazy zařazování vláken **IProvideClassInfo** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5b97d-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="5b97d-155">Pokud zadaná, používá zařazování **ITypeInfo** vrácená z **IProvideClassInfo.GetClassinfo** k určení CLSID třídy vystavení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5b97d-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="5b97d-156">Zařazování lze CLSID vyhledat metadata pro obálku.</span><span class="sxs-lookup"><span data-stu-id="5b97d-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3.  <span data-ttu-id="5b97d-157">Pokud stále zařazování nemůže určovat třídu, zabalí rozhraní s obecné obálku třídy s názvem **System.__ComObject**.</span><span class="sxs-lookup"><span data-stu-id="5b97d-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="5b97d-158">Výchozí zařazování pro delegáti</span><span class="sxs-lookup"><span data-stu-id="5b97d-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="5b97d-159">Spravované delegáta je zařazené jako rozhraní modelu COM nebo jako ukazatel na funkci založené na mechanismu volání:</span><span class="sxs-lookup"><span data-stu-id="5b97d-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
-   <span data-ttu-id="5b97d-160">Pro platformu vyvolání, delegáta je zařazené jako ukazatel Nespravované funkce ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="5b97d-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
-   <span data-ttu-id="5b97d-161">Pro zprostředkovatele komunikace s objekty COM, je delegáta zařazené jako rozhraní modelu COM typu **_Delegate** ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="5b97d-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="5b97d-162">**_Delegate** rozhraní je definována v knihovně typů Mscorlib.tlb a obsahuje <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> metodu, která umožňuje volat metodu, která odkazuje na delegát.</span><span class="sxs-lookup"><span data-stu-id="5b97d-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="5b97d-163">V následující tabulce jsou zařazování možnosti pro datový typ spravovaného delegáta.</span><span class="sxs-lookup"><span data-stu-id="5b97d-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="5b97d-164"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnoty výčtu k zařazení delegáti.</span><span class="sxs-lookup"><span data-stu-id="5b97d-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="5b97d-165">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="5b97d-165">Enumeration type</span></span>|<span data-ttu-id="5b97d-166">Popis nespravované formátu</span><span class="sxs-lookup"><span data-stu-id="5b97d-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="5b97d-167">**UnmanagedType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="5b97d-167">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="5b97d-168">Ukazatel Nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="5b97d-168">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="5b97d-169">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="5b97d-169">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="5b97d-170">Rozhraní typu **_Delegate**, jak jsou definovány v Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="5b97d-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="5b97d-171">Vezměte v úvahu následující příklad kódu, ve kterém metody `DelegateTestInterface` jsou vyexportovány do knihovny typů COM.</span><span class="sxs-lookup"><span data-stu-id="5b97d-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="5b97d-172">Všimněte si, že pouze deleguje označené jako **ref** (nebo **ByRef**) – klíčové slovo jsou předávány jako vstupně -výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="5b97d-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
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
  
### <a name="type-library-representation"></a><span data-ttu-id="5b97d-173">Typ knihovny reprezentace</span><span class="sxs-lookup"><span data-stu-id="5b97d-173">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="5b97d-174">Ukazatel na funkci můžete přímo odkázat, stejně jako všechny ostatní nespravované – ukazatel na funkci můžete zrušením odkazu.</span><span class="sxs-lookup"><span data-stu-id="5b97d-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b97d-175">Odkaz na ukazatel funkce na spravované delegáta držené nespravovaného kódu nezabrání modul common language runtime v provádění uvolňování paměti na spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="5b97d-175">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="5b97d-176">Například následující kód je nesprávný protože odkaz na `cb` předaný objekt `SetChangeHandler` metody nezachovat `cb` zachování připojení mimo dobu životnosti `Test` metoda.</span><span class="sxs-lookup"><span data-stu-id="5b97d-176">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="5b97d-177">Jednou `cb` objekt uvolnění z paměti, ukazatel na funkci předaný `SetChangeHandler` již není platný.</span><span class="sxs-lookup"><span data-stu-id="5b97d-177">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
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
  
 <span data-ttu-id="5b97d-178">Pro kompenzaci neočekávané uvolňování paměti, volající musíte zajistit, aby `cb` objektu je udržováno aktivní, dokud ukazatel Nespravované funkce je používán.</span><span class="sxs-lookup"><span data-stu-id="5b97d-178">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="5b97d-179">Volitelně může mít nespravovaného kódu upozornit spravovaného kódu, pokud ukazatel na funkci již nepotřebujete, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="5b97d-179">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
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
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="5b97d-180">Výchozí zařazování pro typy hodnot</span><span class="sxs-lookup"><span data-stu-id="5b97d-180">Default marshaling for value types</span></span>  
 <span data-ttu-id="5b97d-181">Většina typy hodnot, jako je například celá čísla a čísla s plovoucí desetinnou čárkou, jsou [přenositelné](../../../docs/framework/interop/blittable-and-non-blittable-types.md) a nevyžadují zařazování.</span><span class="sxs-lookup"><span data-stu-id="5b97d-181">Most value types, such as integers and floating-point numbers, are [blittable](../../../docs/framework/interop/blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="5b97d-182">Další [nepřenositelné](../../../docs/framework/interop/blittable-and-non-blittable-types.md) typy mají odlišné reprezentace v paměti spravovanými a nespravovanými a vyžadují kódování.</span><span class="sxs-lookup"><span data-stu-id="5b97d-182">Other [non-blittable](../../../docs/framework/interop/blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="5b97d-183">Jiné typy stále vyžadují explicitní formátování mezi součinnosti hranic.</span><span class="sxs-lookup"><span data-stu-id="5b97d-183">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="5b97d-184">Toto téma obsahuje informace postupujte podle kroků pro typy formátovanou hodnotu:</span><span class="sxs-lookup"><span data-stu-id="5b97d-184">This topic provides the follow information on formatted value types:</span></span>  
  
-   [<span data-ttu-id="5b97d-185">Typy hodnot, které jsou používány platformy vyvolání</span><span class="sxs-lookup"><span data-stu-id="5b97d-185">Value Types Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforvaluetypesanchor2)  
  
-   [<span data-ttu-id="5b97d-186">Typy hodnot, které jsou používány zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="5b97d-186">Value Types Used in COM Interop</span></span>](#cpcondefaultmarshalingforvaluetypesanchor3)  
  
 <span data-ttu-id="5b97d-187">Kromě popisující formátovaný typy, toto téma popisuje [typy hodnot systému](#cpcondefaultmarshalingforvaluetypesanchor1) které mají neobvyklé chování zařazování.</span><span class="sxs-lookup"><span data-stu-id="5b97d-187">In addition to describing formatted types, this topic identifies [System Value Types](#cpcondefaultmarshalingforvaluetypesanchor1) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="5b97d-188">Formátovaný typ je komplexní typ, který obsahuje informace, které explicitně určuje rozložení její členy v paměti.</span><span class="sxs-lookup"><span data-stu-id="5b97d-188">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="5b97d-189">Informace o rozvržení člen je prováděno pomocí <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="5b97d-189">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="5b97d-190">Rozložení může být jedna z následujících <xref:System.Runtime.InteropServices.LayoutKind> hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="5b97d-190">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
-   <span data-ttu-id="5b97d-191">**LayoutKind.Automatic**</span><span class="sxs-lookup"><span data-stu-id="5b97d-191">**LayoutKind.Automatic**</span></span>  
  
     <span data-ttu-id="5b97d-192">Označuje, že je modul common language runtime volné chcete změnit pořadí členů typ efektivitu.</span><span class="sxs-lookup"><span data-stu-id="5b97d-192">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="5b97d-193">Pokud však typ hodnoty je předán nespravovaného kódu, rozložení členy nebude předvídatelný.</span><span class="sxs-lookup"><span data-stu-id="5b97d-193">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="5b97d-194">Pokus o zařazování tato struktura automaticky dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="5b97d-194">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
-   <span data-ttu-id="5b97d-195">**LayoutKind.Sequential**</span><span class="sxs-lookup"><span data-stu-id="5b97d-195">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="5b97d-196">Označuje, že členy typu jsou k nastíněny v nespravované paměti ve stejném pořadí, ve kterém se zobrazí v definici spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="5b97d-196">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
-   <span data-ttu-id="5b97d-197">**LayoutKind.Explicit**</span><span class="sxs-lookup"><span data-stu-id="5b97d-197">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="5b97d-198">Označuje, že členové jsou nastíněny podle <xref:System.Runtime.InteropServices.FieldOffsetAttribute> součástí každého pole.</span><span class="sxs-lookup"><span data-stu-id="5b97d-198">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor2"></a>   
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="5b97d-199">Typy hodnot, které jsou používány platformy vyvolání</span><span class="sxs-lookup"><span data-stu-id="5b97d-199">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="5b97d-200">V následujícím příkladu `Point` a `Rect` typy poskytovat člen informace o rozložení pomocí **StructLayoutAttribute**.</span><span class="sxs-lookup"><span data-stu-id="5b97d-200">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
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
  
 <span data-ttu-id="5b97d-201">Při zařazen do nespravovaného kódu, tyto formátovaný typy jsou zařazené jako struktury stylu jazyka C.</span><span class="sxs-lookup"><span data-stu-id="5b97d-201">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="5b97d-202">To poskytuje snadný způsob volání nespravovaného rozhraní API, která má struktura argumenty.</span><span class="sxs-lookup"><span data-stu-id="5b97d-202">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="5b97d-203">Například `POINT` a `RECT` struktury se dá předat do rozhraní API Win32 Microsoft **PtInRect** funkce následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5b97d-203">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Win32 API **PtInRect** function as follows:</span></span>  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="5b97d-204">Abyste mohli předávat struktury používá následující platforma vyvolání definice:</span><span class="sxs-lookup"><span data-stu-id="5b97d-204">You can pass structures using the following platform invoke definition:</span></span>  
  
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
  
 <span data-ttu-id="5b97d-205">`Rect` Typ hodnoty musí být předán odkazem, protože očekává ukazatel na nespravovaného rozhraní API `RECT` mají být předány funkce.</span><span class="sxs-lookup"><span data-stu-id="5b97d-205">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="5b97d-206">`Point` Typ hodnoty je předaná hodnota protože očekává nespravovaného rozhraní API `POINT` mají být předány v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="5b97d-206">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="5b97d-207">Tento jemně rozdíl je velmi důležité.</span><span class="sxs-lookup"><span data-stu-id="5b97d-207">This subtle difference is very important.</span></span> <span data-ttu-id="5b97d-208">Odkazy jsou předány na nespravovaný kód jako ukazatele.</span><span class="sxs-lookup"><span data-stu-id="5b97d-208">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="5b97d-209">Hodnoty jsou předávány nespravovaného kódu v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="5b97d-209">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b97d-210">Když formátovaný typ se zařadit jako strukturu, jsou přístupné pouze pole v rámci typu.</span><span class="sxs-lookup"><span data-stu-id="5b97d-210">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="5b97d-211">Pokud má typ metody, vlastnosti nebo události, jsou nedostupná z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5b97d-211">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="5b97d-212">Třídy můžete také zařazeno na nespravovaný kód jako stylu jazyka C struktury zadaný opravení člen rozložení.</span><span class="sxs-lookup"><span data-stu-id="5b97d-212">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="5b97d-213">Informace o třídě rozložení člen je také součástí <xref:System.Runtime.InteropServices.StructLayoutAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="5b97d-213">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="5b97d-214">Hlavní rozdíl mezi typy hodnot s pevné rozložení a tříd pomocí pevné rozložení je způsob, ve kterém jsou zařazené na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="5b97d-214">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="5b97d-215">Typy hodnot se předávají hodnotou (v zásobníku) a v důsledku toho nejsou vidět všechny změny provedené u členů typu volaného volající.</span><span class="sxs-lookup"><span data-stu-id="5b97d-215">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="5b97d-216">Odkazové typy jsou předaná odkaz (odkaz na typ je předán v zásobníku); v důsledku toho jsou všechny změny provedené volaného na členy typu blittable typu pohledu volající.</span><span class="sxs-lookup"><span data-stu-id="5b97d-216">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b97d-217">Pokud odkazového typu členy nepřenositelné typy, převod je požadovaná dvakrát: poprvé, když je argument předaný nespravované straně a druhý čas na vrátit z volání.</span><span class="sxs-lookup"><span data-stu-id="5b97d-217">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="5b97d-218">Z důvodu to přidat režie vstup/výstup parametry musí explicitně u argument v případě volající chce vidět změny provedené volaného.</span><span class="sxs-lookup"><span data-stu-id="5b97d-218">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="5b97d-219">V následujícím příkladu `SystemTime` třída má sekvenční člen rozložení a se dá předat do rozhraní API Win32 **GetSystemTime** funkce.</span><span class="sxs-lookup"><span data-stu-id="5b97d-219">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Win32 API **GetSystemTime** function.</span></span>  
  
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
  
 <span data-ttu-id="5b97d-220">**GetSystemTime** funkce je definován následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5b97d-220">The **GetSystemTime** function is defined as follows:</span></span>  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="5b97d-221">Definice pro vyvolání ekvivalentní platformy **GetSystemTime** vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="5b97d-221">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
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
  
 <span data-ttu-id="5b97d-222">Všimněte si, že `SystemTime` argument není zadán jako argument typu odkaz, protože `SystemTime` je třída, není typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5b97d-222">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="5b97d-223">Na rozdíl od typy hodnot jsou vždy třídy předán odkazem.</span><span class="sxs-lookup"><span data-stu-id="5b97d-223">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="5b97d-224">Následující příklad kódu ukazuje jiné `Point` třídu, která má metodu s názvem `SetXY`.</span><span class="sxs-lookup"><span data-stu-id="5b97d-224">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="5b97d-225">Protože má tento typ sekvenční rozložení, můžete předaný nespravovaného kódu a zařazené jako strukturu.</span><span class="sxs-lookup"><span data-stu-id="5b97d-225">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="5b97d-226">Ale `SetXY` člen není možné volat z nespravovaného kódu, i když je objekt předaný odkazem.</span><span class="sxs-lookup"><span data-stu-id="5b97d-226">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
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
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="5b97d-227">Typy hodnot, které jsou používány zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="5b97d-227">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="5b97d-228">Formátovaný typy lze předat také volání metody zprostředkovatele komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="5b97d-228">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="5b97d-229">Ve skutečnosti při exportu do knihovny typů, typů hodnot se automaticky převedou na struktury.</span><span class="sxs-lookup"><span data-stu-id="5b97d-229">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="5b97d-230">Jak ukazuje následující příklad, `Point` typ hodnoty se změní na definici typu (typedef) s názvem `Point`.</span><span class="sxs-lookup"><span data-stu-id="5b97d-230">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="5b97d-231">Všechny odkazy na `Point` typ hodnoty jinde v knihovně typů jsou nahrazeny `Point` typedef.</span><span class="sxs-lookup"><span data-stu-id="5b97d-231">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="5b97d-232">**Typ knihovny reprezentace**</span><span class="sxs-lookup"><span data-stu-id="5b97d-232">**Type library representation**</span></span>  
  
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
  
 <span data-ttu-id="5b97d-233">Stejná pravidla použitý k zařazování hodnoty a odkazy na platformě vyvolat volání se používají při zařazování prostřednictvím rozhraní modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5b97d-233">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="5b97d-234">Například když instanci `Point` typ hodnoty je předán z rozhraní .NET Framework do modelu COM, `Point` je předaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="5b97d-234">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="5b97d-235">Pokud `Point` typ hodnoty je předán odkazem ukazatel na `Point` je předán v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="5b97d-235">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="5b97d-236">Spolupráce vláken nepodporuje vyšší úrovně dereference (**bodu \* \*** ) v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="5b97d-236">The interop marshaler does not support higher levels of indirection (**Point \*\***) in either direction.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b97d-237">Struktury, že <xref:System.Runtime.InteropServices.LayoutKind> nastavena na hodnotu výčtu **explicitní** nelze použít v zprostředkovatel komunikace s objekty COM, protože knihovny exportovaný typů nelze express explicitní rozložení.</span><span class="sxs-lookup"><span data-stu-id="5b97d-237">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor1"></a>   
### <a name="system-value-types"></a><span data-ttu-id="5b97d-238">Typy hodnot systému</span><span class="sxs-lookup"><span data-stu-id="5b97d-238">System Value Types</span></span>  
 <span data-ttu-id="5b97d-239"><xref:System> Oboru názvů má několik typů hodnoty, které představují zabalené formu runtime primitivní typy.</span><span class="sxs-lookup"><span data-stu-id="5b97d-239">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="5b97d-240">Například hodnota typu <xref:System.Int32?displayProperty=nameWithType> struktura představuje zabalené formu **ELEMENT_TYPE_I4**.</span><span class="sxs-lookup"><span data-stu-id="5b97d-240">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="5b97d-241">Místo zařazování tyto typy jako struktury, jako jsou i další typy formátovaný, můžete zařazování je stejným způsobem jako primitivní typy, které budou pole.</span><span class="sxs-lookup"><span data-stu-id="5b97d-241">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="5b97d-242">**System.Int32** je proto zařazené jako **ELEMENT_TYPE_I4** místo jako strukturu obsahující jednoho člena typu **dlouho**.</span><span class="sxs-lookup"><span data-stu-id="5b97d-242">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="5b97d-243">Následující tabulka obsahuje seznam typů hodnot v **systému** obor názvů, které jsou pevně určené reprezentace primitivní typy.</span><span class="sxs-lookup"><span data-stu-id="5b97d-243">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="5b97d-244">Typ hodnoty systému</span><span class="sxs-lookup"><span data-stu-id="5b97d-244">System value type</span></span>|<span data-ttu-id="5b97d-245">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="5b97d-245">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="5b97d-246">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="5b97d-246">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="5b97d-247">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="5b97d-247">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="5b97d-248">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="5b97d-248">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="5b97d-249">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="5b97d-249">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="5b97d-250">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="5b97d-250">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="5b97d-251">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="5b97d-251">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="5b97d-252">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="5b97d-252">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="5b97d-253">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="5b97d-253">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="5b97d-254">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="5b97d-254">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="5b97d-255">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="5b97d-255">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="5b97d-256">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="5b97d-256">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="5b97d-257">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="5b97d-257">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="5b97d-258">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="5b97d-258">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="5b97d-259">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="5b97d-259">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="5b97d-260">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="5b97d-260">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="5b97d-261">Jinou hodnotu typy, které do **systému** obor názvů jsou zpracovány jinak.</span><span class="sxs-lookup"><span data-stu-id="5b97d-261">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="5b97d-262">Protože nespravovaného kódu už má zavedené formátů pro tyto typy, zařazování má zvláštní pravidla pro zařazování je.</span><span class="sxs-lookup"><span data-stu-id="5b97d-262">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="5b97d-263">Následující tabulka uvádí typy speciální hodnot v **systému** obor názvů, a také nespravovaný typ jsou zařazené do.</span><span class="sxs-lookup"><span data-stu-id="5b97d-263">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="5b97d-264">Typ hodnoty systému</span><span class="sxs-lookup"><span data-stu-id="5b97d-264">System value type</span></span>|<span data-ttu-id="5b97d-265">Typ IDL</span><span class="sxs-lookup"><span data-stu-id="5b97d-265">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="5b97d-266">**DATUM**</span><span class="sxs-lookup"><span data-stu-id="5b97d-266">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="5b97d-267">**DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="5b97d-267">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="5b97d-268">**GUID**</span><span class="sxs-lookup"><span data-stu-id="5b97d-268">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="5b97d-269">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="5b97d-269">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="5b97d-270">Následující kód ukazuje definici nespravované typy **datum**, **GUID**, **DECIMAL**, a **OLE_COLOR** v Stdole2 typu Knihovna.</span><span class="sxs-lookup"><span data-stu-id="5b97d-270">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="5b97d-271">Typ knihovny reprezentace</span><span class="sxs-lookup"><span data-stu-id="5b97d-271">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="5b97d-272">Následující kód ukazuje odpovídající definice v spravovaný `IValueTypes` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5b97d-272">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
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
  
#### <a name="type-library-representation"></a><span data-ttu-id="5b97d-273">Typ knihovny reprezentace</span><span class="sxs-lookup"><span data-stu-id="5b97d-273">Type library representation</span></span>  
  
```  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="5b97d-274">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b97d-274">See Also</span></span>  
 [<span data-ttu-id="5b97d-275">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="5b97d-275">Blittable and Non-Blittable Types</span></span>](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [<span data-ttu-id="5b97d-276">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="5b97d-276">Copying and Pinning</span></span>](../../../docs/framework/interop/copying-and-pinning.md)  
 [<span data-ttu-id="5b97d-277">Výchozí zařazování pro pole</span><span class="sxs-lookup"><span data-stu-id="5b97d-277">Default Marshaling for Arrays</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)  
 [<span data-ttu-id="5b97d-278">Výchozí zařazování pro objekty</span><span class="sxs-lookup"><span data-stu-id="5b97d-278">Default Marshaling for Objects</span></span>](../../../docs/framework/interop/default-marshaling-for-objects.md)  
 [<span data-ttu-id="5b97d-279">Výchozí zařazování pro řetězce</span><span class="sxs-lookup"><span data-stu-id="5b97d-279">Default Marshaling for Strings</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)
