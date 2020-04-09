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
ms.openlocfilehash: f7df323dacfbee3361fe75d831f1e87df328b194
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989217"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="cf551-102">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="cf551-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="cf551-103">Interop zařazování pracuje na pravidla, která určují, jak se chovají data spojená s parametry metody, jak prochází mezi spravované a nespravované paměti.</span><span class="sxs-lookup"><span data-stu-id="cf551-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="cf551-104">Tato předdefinovaná pravidla řídí takové zařazovací aktivity jako transformace datového typu, zda volaný může změnit data předávaná a vrátit tyto změny volajícímu a za jakých okolností zařazování poskytuje optimalizace výkonu.</span><span class="sxs-lookup"><span data-stu-id="cf551-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="cf551-105">Tato část identifikuje výchozí charakteristiky chování interop zařazování služby.</span><span class="sxs-lookup"><span data-stu-id="cf551-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="cf551-106">Představuje podrobné informace o zařazování polí, booleovské typy, char typy, delegáti, třídy, objekty, řetězce a struktury.</span><span class="sxs-lookup"><span data-stu-id="cf551-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf551-107">Zařazování obecných typů není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cf551-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="cf551-108">Další informace naleznete v tématu [Spolupráce pomocí obecných typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cf551-108">For more information see, [Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="cf551-109">Správa paměti s interop zařazovacím zařízením</span><span class="sxs-lookup"><span data-stu-id="cf551-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="cf551-110">Interop zařazovací vždy pokusí uvolnit paměť přidělenou nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="cf551-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="cf551-111">Toto chování je v souladu s pravidly správy paměti modelu COM, ale liší se od pravidel, která řídí nativní C++.</span><span class="sxs-lookup"><span data-stu-id="cf551-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="cf551-112">Zmatek může vzniknout, pokud očekáváte nativní chování jazyka C++ (bez uvolnění paměti) při použití platformy invoke, která automaticky uvolní paměť pro ukazatele.</span><span class="sxs-lookup"><span data-stu-id="cf551-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="cf551-113">Například volání následující nespravované metody z dll C++ automaticky neuvolní žádnou paměť.</span><span class="sxs-lookup"><span data-stu-id="cf551-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="cf551-114">Nespravovaný podpis</span><span class="sxs-lookup"><span data-stu-id="cf551-114">Unmanaged signature</span></span>  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="cf551-115">Pokud však definujete metodu jako platformu vyvolat prototyp, <xref:System.String> nahraďte `MethodOne`každý typ **BSTR** typem `b` a volání , běžný jazyk runtime pokusí uvolnit dvakrát.</span><span class="sxs-lookup"><span data-stu-id="cf551-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="cf551-116">Chování zařazování můžete <xref:System.IntPtr> změnit pomocí typů, nikoli typů **String.**</span><span class="sxs-lookup"><span data-stu-id="cf551-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="cf551-117">Runtime vždy používá **CoTaskMemFree** metoda uvolnit paměť.</span><span class="sxs-lookup"><span data-stu-id="cf551-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="cf551-118">Pokud paměť, se kterou pracujete, nebyla přidělena metodou **CoTaskMemAlloc,** musíte použít **IntPtr** a uvolnit paměť ručně pomocí příslušné metody.</span><span class="sxs-lookup"><span data-stu-id="cf551-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="cf551-119">Podobně se můžete vyhnout automatickému uvolnění paměti v situacích, kdy by paměť neměla být nikdy uvolněna, například při použití funkce **GetCommandLine** z kernel32.dll, která vrací ukazatel na paměť jádra.</span><span class="sxs-lookup"><span data-stu-id="cf551-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="cf551-120">Podrobnosti o ručním uvolnění paměti naleznete v [tématu Ukázka vyrovnávacích pamětí](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cf551-120">For details on manually freeing memory, see the [Buffers Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="cf551-121">Výchozí zařazování pro třídy</span><span class="sxs-lookup"><span data-stu-id="cf551-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="cf551-122">Třídy mohou být zařazeny pouze pomocí interop com a jsou vždy zařazeny jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cf551-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="cf551-123">V některých případech rozhraní slouží k zařazovací třídy je označována jako rozhraní třídy.</span><span class="sxs-lookup"><span data-stu-id="cf551-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="cf551-124">Informace o přepsání rozhraní třídy s rozhraním podle vašeho výběru naleznete [v tématu Zavedení rozhraní třídy](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="cf551-124">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="cf551-125">Předávání tříd com</span><span class="sxs-lookup"><span data-stu-id="cf551-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="cf551-126">Pokud je spravovaná třída předána com, interop zařazování automaticky zabalí třídu s proxy com a předá rozhraní třídy vytvořené proxy volání metody COM.</span><span class="sxs-lookup"><span data-stu-id="cf551-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="cf551-127">Proxy pak deleguje všechna volání na rozhraní třídy zpět na spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="cf551-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="cf551-128">Proxy také zveřejňuje další rozhraní, které nejsou explicitně implementovány třídy.</span><span class="sxs-lookup"><span data-stu-id="cf551-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="cf551-129">Proxy server automaticky implementuje rozhraní, jako je **Například IUnknown** a **IDispatch** jménem třídy.</span><span class="sxs-lookup"><span data-stu-id="cf551-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="cf551-130">Předávání tříd do kódu .NET</span><span class="sxs-lookup"><span data-stu-id="cf551-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="cf551-131">Coclasses nejsou obvykle používány jako argumenty metody v com.</span><span class="sxs-lookup"><span data-stu-id="cf551-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="cf551-132">Místo toho je výchozí rozhraní obvykle předáno místo coclass.</span><span class="sxs-lookup"><span data-stu-id="cf551-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="cf551-133">Při předání rozhraní do spravovaného kódu interop zařazovací modul je zodpovědný za zabalení rozhraní s správné obálky a předání obálky spravované metody.</span><span class="sxs-lookup"><span data-stu-id="cf551-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="cf551-134">Určení, který obal použít může být obtížné.</span><span class="sxs-lookup"><span data-stu-id="cf551-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="cf551-135">Každá instance objektu COM má jeden jedinečný obal bez ohledu na to, kolik rozhraní objekt implementuje.</span><span class="sxs-lookup"><span data-stu-id="cf551-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="cf551-136">Například jeden objekt COM, který implementuje pět odlišných rozhraní má pouze jeden obálku.</span><span class="sxs-lookup"><span data-stu-id="cf551-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="cf551-137">Stejný obálka zveřejňuje všech pět rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cf551-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="cf551-138">Pokud jsou vytvořeny dvě instance objektu COM, pak jsou vytvořeny dvě instance obálky.</span><span class="sxs-lookup"><span data-stu-id="cf551-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="cf551-139">Aby obálka zachovala stejný typ po celou dobu jeho životnosti, zařazovací modul interop musí identifikovat správné obálky při prvním průchodu rozhraní vystaveného objektem prostřednictvím zařazovacího modulu.</span><span class="sxs-lookup"><span data-stu-id="cf551-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="cf551-140">Zařazovací objekt identifikuje objekt při pohledu na jedno z rozhraní, které objekt implementuje.</span><span class="sxs-lookup"><span data-stu-id="cf551-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="cf551-141">Například zařazování určuje, že obálka třídy by měla být použita k zalomení rozhraní, které bylo předáno do spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="cf551-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="cf551-142">Při prvním předání rozhraní prostřednictvím zařazovacího modulu zařazovací modul, zařazovací objekt zkontroluje, zda rozhraní pochází ze známého objektu.</span><span class="sxs-lookup"><span data-stu-id="cf551-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="cf551-143">Tato kontrola se vyskytuje ve dvou situacích:</span><span class="sxs-lookup"><span data-stu-id="cf551-143">This check occurs in two situations:</span></span>  
  
- <span data-ttu-id="cf551-144">Rozhraní je implementováno jiným spravovaným objektem, který byl předán com jinde.</span><span class="sxs-lookup"><span data-stu-id="cf551-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="cf551-145">Zařazovací modul může snadno identifikovat rozhraní vystavená spravovanými objekty a je schopen spárovat rozhraní se spravovaným objektem, který poskytuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="cf551-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="cf551-146">Spravovaný objekt je pak předán metodě a není potřeba žádné obálky.</span><span class="sxs-lookup"><span data-stu-id="cf551-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
- <span data-ttu-id="cf551-147">Objekt, který již byl zabalen, implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cf551-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="cf551-148">Chcete-li zjistit, zda se jedná o tento případ, zařazovací zařízení dotazuje objekt pro jeho **rozhraní IUnknown** a porovná vrácené rozhraní rozhraní jiných objektů, které jsou již zabaleny.</span><span class="sxs-lookup"><span data-stu-id="cf551-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="cf551-149">Pokud je rozhraní stejné jako u jiné obálky, objekty mají stejnou identitu a existující obálka je předána metodě.</span><span class="sxs-lookup"><span data-stu-id="cf551-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="cf551-150">Pokud rozhraní není z známého objektu, zařazovací provádí následující akce:</span><span class="sxs-lookup"><span data-stu-id="cf551-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1. <span data-ttu-id="cf551-151">Zařazovací objekt dotazuje objekt pro rozhraní **IProvideClassInfo2.**</span><span class="sxs-lookup"><span data-stu-id="cf551-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="cf551-152">Pokud je k dispozici, zařazování používá CLSID vrácené z **IProvideClassInfo2.GetGUID** k identifikaci coclass poskytující rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cf551-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="cf551-153">Pomocí CLSID zařazování můžete vyhledat obálku z registru, pokud sestavení bylo dříve registrováno.</span><span class="sxs-lookup"><span data-stu-id="cf551-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2. <span data-ttu-id="cf551-154">Zařazovací zařízení dotazuje rozhraní pro rozhraní **IProvideClassInfo.**</span><span class="sxs-lookup"><span data-stu-id="cf551-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="cf551-155">Pokud je k dispozici, zařazování používá **ITypeInfo** vrácené z **IProvideClassInfo.GetClassinfo** k určení CLSID třídy vystavení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cf551-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="cf551-156">Zařazování můžete použít CLSID vyhledejte metadata pro obálku.</span><span class="sxs-lookup"><span data-stu-id="cf551-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3. <span data-ttu-id="cf551-157">Pokud zařazování stále nemůže identifikovat třídu, zabalí rozhraní s obecnou třídou obálky nazvanou **System.__ComObject**.</span><span class="sxs-lookup"><span data-stu-id="cf551-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="cf551-158">Výchozí zařazování delegátů</span><span class="sxs-lookup"><span data-stu-id="cf551-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="cf551-159">Spravovaný delegát je zařazen jako rozhraní COM nebo jako ukazatel funkce na základě volajícího mechanismu:</span><span class="sxs-lookup"><span data-stu-id="cf551-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
- <span data-ttu-id="cf551-160">Pro vyvolání platformy delegát adekvátní je zařazen jako ukazatel nespravované funkce ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="cf551-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
- <span data-ttu-id="cf551-161">Pro interop COM delegát je zařazen jako com rozhraní typu **_Delegate** ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="cf551-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="cf551-162">Rozhraní **_Delegate** je definováno v knihovně typů Mscorlib.tlb a obsahuje metodu, <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> která umožňuje volat metodu, na kterou delegát odkazuje.</span><span class="sxs-lookup"><span data-stu-id="cf551-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="cf551-163">V následující tabulce jsou uvedeny možnosti zařazování pro datový typ spravovaného delegáta.</span><span class="sxs-lookup"><span data-stu-id="cf551-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="cf551-164">Atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> poskytuje <xref:System.Runtime.InteropServices.UnmanagedType> několik hodnot výčtu pro delegáty zařazování.</span><span class="sxs-lookup"><span data-stu-id="cf551-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="cf551-165">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="cf551-165">Enumeration type</span></span>|<span data-ttu-id="cf551-166">Popis nespravovaného formátu</span><span class="sxs-lookup"><span data-stu-id="cf551-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="cf551-167">**UnmanagedType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="cf551-167">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="cf551-168">Ukazatel nespravované funkce.</span><span class="sxs-lookup"><span data-stu-id="cf551-168">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="cf551-169">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="cf551-169">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="cf551-170">Rozhraní typu **_Delegate**, jak je definováno v mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="cf551-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="cf551-171">Zvažte následující příklad kódu, `DelegateTestInterface` ve kterém jsou metody exportovány do knihovny typů COM.</span><span class="sxs-lookup"><span data-stu-id="cf551-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="cf551-172">Všimněte si, že pouze delegáti označené **ref** (nebo **ByRef**) klíčové slovo jsou předány jako In/Out parametry.</span><span class="sxs-lookup"><span data-stu-id="cf551-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
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
  
### <a name="type-library-representation"></a><span data-ttu-id="cf551-173">Reprezentace knihovny typů</span><span class="sxs-lookup"><span data-stu-id="cf551-173">Type library representation</span></span>  
  
```cpp  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 <span data-ttu-id="cf551-174">Ukazatel funkce může být odkazován, stejně jako jakýkoli jiný ukazatel nespravované funkce může být dereferenced.</span><span class="sxs-lookup"><span data-stu-id="cf551-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="cf551-175">V tomto příkladu při dva delegáti jsou zařazeny jako <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, výsledkem `int` je a ukazatel na . `int`</span><span class="sxs-lookup"><span data-stu-id="cf551-175">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="cf551-176">Vzhledem k tomu, `int` že jsou zařazovány typy delegátů, představuje zde ukazatel na void (`void*`), což je adresa delegáta v paměti.</span><span class="sxs-lookup"><span data-stu-id="cf551-176">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="cf551-177">Jinými slovy, tento výsledek je specifický pro 32bitové systémy Windows, protože `int` zde představuje velikost ukazatele funkce.</span><span class="sxs-lookup"><span data-stu-id="cf551-177">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="cf551-178">Odkaz na ukazatel funkce na spravovaného delegáta drženého nespravovaným kódem nebrání tomu, aby soubor RUNTIME společného jazyka provedl uvolňování paměti spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="cf551-178">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="cf551-179">Například následující kód je nesprávný, `cb` protože odkaz na `SetChangeHandler` objekt, předaný metodě, neudržuje `cb` naživu mimo životnost `Test` metody.</span><span class="sxs-lookup"><span data-stu-id="cf551-179">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="cf551-180">Jakmile `cb` je objekt uvolněn, ukazatel funkce `SetChangeHandler` předaný již není platný.</span><span class="sxs-lookup"><span data-stu-id="cf551-180">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
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
  
 <span data-ttu-id="cf551-181">Chcete-li kompenzovat neočekávané uvolnění paměti, volající musí zajistit, že `cb` objekt je udržována naživu tak dlouho, dokud nespravované funkce ukazatel je používán.</span><span class="sxs-lookup"><span data-stu-id="cf551-181">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="cf551-182">Volitelně můžete mít nespravovaný kód upozornit spravovaný kód, když ukazatel funkce již není potřeba, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="cf551-182">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
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
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="cf551-183">Výchozí zařazování pro typy hodnot</span><span class="sxs-lookup"><span data-stu-id="cf551-183">Default marshaling for value types</span></span>  
 <span data-ttu-id="cf551-184">Většina typů hodnot, například celá čísla a čísla s plovoucí desetinnou desetinnou hodnotou, jsou [přenositelná](blittable-and-non-blittable-types.md) a nevyžadují zařazování.</span><span class="sxs-lookup"><span data-stu-id="cf551-184">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="cf551-185">Jiné [nepřenositelné](blittable-and-non-blittable-types.md) typy mají odlišné reprezentace ve spravované a nespravované paměti a vyžadují zařazování.</span><span class="sxs-lookup"><span data-stu-id="cf551-185">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="cf551-186">Ještě jiné typy vyžadují explicitní formátování přes hranice spolupráce.</span><span class="sxs-lookup"><span data-stu-id="cf551-186">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="cf551-187">Tato část obsahuje informace o následujících formátovaných typech hodnot:</span><span class="sxs-lookup"><span data-stu-id="cf551-187">This section provides information on the following formatted value types:</span></span>  
  
- [<span data-ttu-id="cf551-188">Typy hodnot používané v vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="cf551-188">Value Types Used in Platform Invoke</span></span>](#value-types-used-in-platform-invoke)  
  
- [<span data-ttu-id="cf551-189">Typy hodnot používané v interopu com</span><span class="sxs-lookup"><span data-stu-id="cf551-189">Value Types Used in COM Interop</span></span>](#value-types-used-in-com-interop)  
  
 <span data-ttu-id="cf551-190">Kromě popisu formátované typy, toto téma identifikuje [typy systémových hodnot,](#system-value-types) které mají neobvyklé zařazování chování.</span><span class="sxs-lookup"><span data-stu-id="cf551-190">In addition to describing formatted types, this topic identifies [System Value Types](#system-value-types) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="cf551-191">Formátovaný typ je komplexní typ, který obsahuje informace, které explicitně řídí rozložení svých členů v paměti.</span><span class="sxs-lookup"><span data-stu-id="cf551-191">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="cf551-192">Informace o rozložení člena jsou <xref:System.Runtime.InteropServices.StructLayoutAttribute> k dispozici pomocí atributu.</span><span class="sxs-lookup"><span data-stu-id="cf551-192">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="cf551-193">Rozložení může být jedna <xref:System.Runtime.InteropServices.LayoutKind> z následujících hodnot výčtu:</span><span class="sxs-lookup"><span data-stu-id="cf551-193">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
- <span data-ttu-id="cf551-194">**LayoutKind.Auto**</span><span class="sxs-lookup"><span data-stu-id="cf551-194">**LayoutKind.Auto**</span></span>  
  
     <span data-ttu-id="cf551-195">Označuje, že běžný jazyk runtime je zdarma ke snížení pořadí členů typu pro efektivitu.</span><span class="sxs-lookup"><span data-stu-id="cf551-195">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="cf551-196">Však při zadání typu hodnoty do nespravovaného kódu, rozložení členů je předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="cf551-196">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="cf551-197">Pokus o zařazovací takové struktury automaticky způsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="cf551-197">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
- <span data-ttu-id="cf551-198">**LayoutKind.Sekvenční**</span><span class="sxs-lookup"><span data-stu-id="cf551-198">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="cf551-199">Označuje, že členy typu mají být rozloženy v nespravované paměti ve stejném pořadí, ve kterém se zobrazí v definici spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="cf551-199">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
- <span data-ttu-id="cf551-200">**LayoutKind.Explicit**</span><span class="sxs-lookup"><span data-stu-id="cf551-200">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="cf551-201">Označuje, že členy jsou rozloženy podle dodaného <xref:System.Runtime.InteropServices.FieldOffsetAttribute> s každým polem.</span><span class="sxs-lookup"><span data-stu-id="cf551-201">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="cf551-202">Typy hodnot používané v vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="cf551-202">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="cf551-203">V následujícím `Point` příkladu `Rect` a typy poskytují informace o rozložení členů pomocí **atributu StructLayoutAttribute**.</span><span class="sxs-lookup"><span data-stu-id="cf551-203">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
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
  
 <span data-ttu-id="cf551-204">Při zařazené do nespravovaného kódu jsou tyto formátované typy zařazeny jako struktury stylu C.</span><span class="sxs-lookup"><span data-stu-id="cf551-204">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="cf551-205">To poskytuje snadný způsob volání nespravovanérozhraní API, které má argumenty struktury.</span><span class="sxs-lookup"><span data-stu-id="cf551-205">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="cf551-206">Například `POINT` a struktury mohou být předány microsoft windows api **PtInRect** funkce takto: `RECT`</span><span class="sxs-lookup"><span data-stu-id="cf551-206">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Windows API **PtInRect** function as follows:</span></span>  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="cf551-207">Můžete předat struktury pomocí následující platformy vyvolat definici:</span><span class="sxs-lookup"><span data-stu-id="cf551-207">You can pass structures using the following platform invoke definition:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 <span data-ttu-id="cf551-208">Typ `Rect` hodnoty musí být předán odkazem, protože nespravované `RECT` rozhraní API očekává ukazatel na a, který má být předán funkci.</span><span class="sxs-lookup"><span data-stu-id="cf551-208">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="cf551-209">Typ `Point` hodnoty je předán hodnotou, protože nespravované rozhraní API očekává, že `POINT` bude předán v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cf551-209">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="cf551-210">Tento jemný rozdíl je velmi důležitý.</span><span class="sxs-lookup"><span data-stu-id="cf551-210">This subtle difference is very important.</span></span> <span data-ttu-id="cf551-211">Odkazy jsou předávány nespravovanému kódu jako ukazatele.</span><span class="sxs-lookup"><span data-stu-id="cf551-211">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="cf551-212">Hodnoty jsou předávány nespravovanému kódu v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cf551-212">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf551-213">Pokud formátovaný typ je zařazen jako struktura, pouze pole v rámci typu jsou přístupné.</span><span class="sxs-lookup"><span data-stu-id="cf551-213">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="cf551-214">Pokud typ má metody, vlastnosti nebo události, jsou nepřístupné z nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="cf551-214">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="cf551-215">Třídy mohou být také zařazeny do nespravovaného kódu jako struktury ve stylu C za předpokladu, že mají pevné rozložení členů.</span><span class="sxs-lookup"><span data-stu-id="cf551-215">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="cf551-216">Informace o rozložení člena pro třídu <xref:System.Runtime.InteropServices.StructLayoutAttribute> jsou také k dispozici s atributem.</span><span class="sxs-lookup"><span data-stu-id="cf551-216">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="cf551-217">Hlavní rozdíl mezi typy hodnot s pevným rozložením a třídami s pevným rozložením je způsob, jakým jsou zařazeny do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="cf551-217">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="cf551-218">Typy hodnot jsou předávány hodnotou (v zásobníku) a následně všechny změny provedené na členy typu volaného nejsou vidět volající.</span><span class="sxs-lookup"><span data-stu-id="cf551-218">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="cf551-219">Typy odkazů jsou předávány odkazem (odkaz na typ je předán v zásobníku); v důsledku toho všechny změny provedené na blittable typu členů typu volaného jsou vidět volajícího.</span><span class="sxs-lookup"><span data-stu-id="cf551-219">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf551-220">Pokud typ odkazu má členy non-přenositelné typy, převod je vyžadován dvakrát: při prvním při předání argumentu na nespravované straně a podruhé při návratu z volání.</span><span class="sxs-lookup"><span data-stu-id="cf551-220">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="cf551-221">Z důvodu této přidané režie In/Out parametry musí být explicitně použita na argument, pokud volající chce zobrazit změny provedené volaným.</span><span class="sxs-lookup"><span data-stu-id="cf551-221">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="cf551-222">V následujícím příkladu `SystemTime` má třída sekvenční rozložení členů a může být předána funkci **GetSystemTime** rozhraní API systému Windows.</span><span class="sxs-lookup"><span data-stu-id="cf551-222">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Windows API **GetSystemTime** function.</span></span>  
  
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
  
 <span data-ttu-id="cf551-223">Funkce **GetSystemTime** je definována takto:</span><span class="sxs-lookup"><span data-stu-id="cf551-223">The **GetSystemTime** function is defined as follows:</span></span>  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="cf551-224">Ekvivalentní definice vyvolání platformy pro **GetSystemTime** je následující:</span><span class="sxs-lookup"><span data-stu-id="cf551-224">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 <span data-ttu-id="cf551-225">Všimněte `SystemTime` si, že argument není zadán `SystemTime` jako referenční argument, protože je třída, nikoli typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cf551-225">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="cf551-226">Na rozdíl od typů hodnot jsou třídy vždy předávány odkazem.</span><span class="sxs-lookup"><span data-stu-id="cf551-226">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="cf551-227">Následující příklad kódu ukazuje `Point` jinou třídu, která má metodu nazvanou `SetXY`.</span><span class="sxs-lookup"><span data-stu-id="cf551-227">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="cf551-228">Vzhledem k tomu, že typ má sekvenční rozložení, může být předán do nespravovaného kódu a zařazen jako struktura.</span><span class="sxs-lookup"><span data-stu-id="cf551-228">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="cf551-229">`SetXY` Člen však není volatelný z nespravovaného kódu, i když je objekt předán odkazem.</span><span class="sxs-lookup"><span data-stu-id="cf551-229">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
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
  
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="cf551-230">Typy hodnot používané v interopu com</span><span class="sxs-lookup"><span data-stu-id="cf551-230">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="cf551-231">Formátované typy lze také předat volání metod interop com.</span><span class="sxs-lookup"><span data-stu-id="cf551-231">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="cf551-232">Ve skutečnosti při exportu do knihovny typů jsou typy hodnot automaticky převedeny na struktury.</span><span class="sxs-lookup"><span data-stu-id="cf551-232">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="cf551-233">Jak ukazuje následující příklad, typ `Point` hodnoty se stane definicí `Point`typu (typedef) s názvem .</span><span class="sxs-lookup"><span data-stu-id="cf551-233">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="cf551-234">Všechny odkazy na `Point` typ hodnoty jinde v knihovně `Point` typů jsou nahrazeny typedef.</span><span class="sxs-lookup"><span data-stu-id="cf551-234">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="cf551-235">**Reprezentace knihovny typů**</span><span class="sxs-lookup"><span data-stu-id="cf551-235">**Type library representation**</span></span>  
  
```cpp  
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
  
 <span data-ttu-id="cf551-236">Stejná pravidla používaná k zařazování hodnot a odkazů na volání vyvolání platformy se používají při zařazování prostřednictvím rozhraní COM.</span><span class="sxs-lookup"><span data-stu-id="cf551-236">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="cf551-237">Například při předání instance `Point` typu hodnoty z rozhraní COM frameworku `Point` .NET, je předána hodnotou.</span><span class="sxs-lookup"><span data-stu-id="cf551-237">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="cf551-238">Pokud `Point` je typ hodnoty předán odkazem, `Point` je v zásobníku předán ukazatel na a.</span><span class="sxs-lookup"><span data-stu-id="cf551-238">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="cf551-239">Interop zařazování nepodporuje vyšší úrovně dereference **(Point)** \* \*v obou směrech.</span><span class="sxs-lookup"><span data-stu-id="cf551-239">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf551-240">Struktury s <xref:System.Runtime.InteropServices.LayoutKind> hodnotou výčtu nastavenou na **explicit** nelze použít v interop u com, protože exportovaná knihovna typů nemůže vyjádřit explicitní rozložení.</span><span class="sxs-lookup"><span data-stu-id="cf551-240">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
### <a name="system-value-types"></a><span data-ttu-id="cf551-241">Typy systémových hodnot</span><span class="sxs-lookup"><span data-stu-id="cf551-241">System Value Types</span></span>  
 <span data-ttu-id="cf551-242">Obor <xref:System> názvů má několik typů hodnot, které představují zabalenou formu primitivních typů runtime.</span><span class="sxs-lookup"><span data-stu-id="cf551-242">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="cf551-243">Například struktura typu <xref:System.Int32?displayProperty=nameWithType> hodnoty představuje zarámečkovou formu **ELEMENT_TYPE_I4**.</span><span class="sxs-lookup"><span data-stu-id="cf551-243">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="cf551-244">Namísto zařazování těchto typů jako struktury, jako jsou jiné formátované typy, zařazujete je stejným způsobem jako primitivní typy, které zadávají.</span><span class="sxs-lookup"><span data-stu-id="cf551-244">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="cf551-245">**System.Int32** je proto zařazen jako **ELEMENT_TYPE_I4** namísto jako struktura obsahující jeden člen typu **long**.</span><span class="sxs-lookup"><span data-stu-id="cf551-245">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="cf551-246">Následující tabulka obsahuje seznam typů hodnot v oboru názvů **Systém,** které jsou v rámečku reprezentace primitivních typů.</span><span class="sxs-lookup"><span data-stu-id="cf551-246">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="cf551-247">Typ systémové hodnoty</span><span class="sxs-lookup"><span data-stu-id="cf551-247">System value type</span></span>|<span data-ttu-id="cf551-248">Typ prvku</span><span class="sxs-lookup"><span data-stu-id="cf551-248">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="cf551-249">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="cf551-249">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="cf551-250">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="cf551-250">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="cf551-251">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="cf551-251">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="cf551-252">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="cf551-252">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="cf551-253">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="cf551-253">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="cf551-254">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="cf551-254">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="cf551-255">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="cf551-255">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="cf551-256">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="cf551-256">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="cf551-257">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="cf551-257">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="cf551-258">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="cf551-258">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="cf551-259">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="cf551-259">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="cf551-260">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="cf551-260">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="cf551-261">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="cf551-261">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="cf551-262">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="cf551-262">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="cf551-263">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="cf551-263">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="cf551-264">Některé další typy hodnot v oboru názvů **systému** jsou zpracovány odlišně.</span><span class="sxs-lookup"><span data-stu-id="cf551-264">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="cf551-265">Vzhledem k tomu, že nespravovaný kód již má dobře zavedené formáty pro tyto typy, zařazování má zvláštní pravidla pro jejich zařazování.</span><span class="sxs-lookup"><span data-stu-id="cf551-265">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="cf551-266">V následující tabulce jsou uvedeny speciální typy hodnot v oboru názvů **Systém** a také nespravovaný typ, do kterého jsou zařazeny.</span><span class="sxs-lookup"><span data-stu-id="cf551-266">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="cf551-267">Typ systémové hodnoty</span><span class="sxs-lookup"><span data-stu-id="cf551-267">System value type</span></span>|<span data-ttu-id="cf551-268">Typ IDL</span><span class="sxs-lookup"><span data-stu-id="cf551-268">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="cf551-269">**Datum**</span><span class="sxs-lookup"><span data-stu-id="cf551-269">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="cf551-270">**Desetinných**</span><span class="sxs-lookup"><span data-stu-id="cf551-270">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="cf551-271">**Identifikátor guid**</span><span class="sxs-lookup"><span data-stu-id="cf551-271">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="cf551-272">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="cf551-272">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="cf551-273">Následující kód zobrazuje definici nespravovaných typů **DATE**, **GUID**, **DECIMAL**a **OLE_COLOR** v knihovně typů Stdole2.</span><span class="sxs-lookup"><span data-stu-id="cf551-273">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="cf551-274">Reprezentace knihovny typů</span><span class="sxs-lookup"><span data-stu-id="cf551-274">Type library representation</span></span>  
  
```cpp  
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
  
 <span data-ttu-id="cf551-275">Následující kód zobrazuje odpovídající definice ve `IValueTypes` spravovaném rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cf551-275">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
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
  
#### <a name="type-library-representation"></a><span data-ttu-id="cf551-276">Reprezentace knihovny typů</span><span class="sxs-lookup"><span data-stu-id="cf551-276">Type library representation</span></span>  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf551-277">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf551-277">See also</span></span>

- [<span data-ttu-id="cf551-278">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="cf551-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="cf551-279">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="cf551-279">Copying and Pinning</span></span>](copying-and-pinning.md)
- [<span data-ttu-id="cf551-280">Výchozí zařazování pro pole</span><span class="sxs-lookup"><span data-stu-id="cf551-280">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)
- [<span data-ttu-id="cf551-281">Výchozí zařazování pro objekty</span><span class="sxs-lookup"><span data-stu-id="cf551-281">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)
- [<span data-ttu-id="cf551-282">Výchozí zařazování pro řetězce</span><span class="sxs-lookup"><span data-stu-id="cf551-282">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
