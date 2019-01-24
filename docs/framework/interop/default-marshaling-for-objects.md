---
title: Výchozí zařazování pro objekty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84a3ea24120a9548c9d1cd2b7b83997a2c849cde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528016"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="cee07-102">Výchozí zařazování pro objekty</span><span class="sxs-lookup"><span data-stu-id="cee07-102">Default Marshaling for Objects</span></span>
<span data-ttu-id="cee07-103">Parametry a pole typu <xref:System.Object?displayProperty=nameWithType> daly vystavit do nespravovaného kódu jako jeden z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="cee07-103">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>  
  
-   <span data-ttu-id="cee07-104">Hodnotu typu variant, když je parametr objekt.</span><span class="sxs-lookup"><span data-stu-id="cee07-104">A variant when the object is a parameter.</span></span>  
  
-   <span data-ttu-id="cee07-105">Rozhraní, když je objekt pole struktury.</span><span class="sxs-lookup"><span data-stu-id="cee07-105">An interface when the object is a structure field.</span></span>  
  
 <span data-ttu-id="cee07-106">Jenom komunikace s objekty COM podporuje zařazování pro typy objektů.</span><span class="sxs-lookup"><span data-stu-id="cee07-106">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="cee07-107">Výchozí chování je zařadit objektů variant modelu COM.</span><span class="sxs-lookup"><span data-stu-id="cee07-107">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="cee07-108">Tato pravidla se vztahují pouze na typ **objekt** a se nedá použít u objektů se silným typem, které jsou odvozeny z **objekt** třídy.</span><span class="sxs-lookup"><span data-stu-id="cee07-108">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>  
  
 <span data-ttu-id="cee07-109">Toto téma obsahuje následující doplňkové informace o zařazování typy objektů:</span><span class="sxs-lookup"><span data-stu-id="cee07-109">This topic provides the following additional information about marshaling object types:</span></span>  
  
-   [<span data-ttu-id="cee07-110">Zařazování možnosti</span><span class="sxs-lookup"><span data-stu-id="cee07-110">Marshaling Options</span></span>](#cpcondefaultmarshalingforobjectsanchor7)  
  
-   [<span data-ttu-id="cee07-111">Zařazování objektu rozhraní</span><span class="sxs-lookup"><span data-stu-id="cee07-111">Marshaling Object to Interface</span></span>](#cpcondefaultmarshalingforobjectsanchor2)  
  
-   [<span data-ttu-id="cee07-112">Zařazování objektu Variant</span><span class="sxs-lookup"><span data-stu-id="cee07-112">Marshaling Object to Variant</span></span>](#cpcondefaultmarshalingforobjectsanchor3)  
  
-   [<span data-ttu-id="cee07-113">Zařazování typu Variant pro objekt</span><span class="sxs-lookup"><span data-stu-id="cee07-113">Marshaling Variant to Object</span></span>](#cpcondefaultmarshalingforobjectsanchor4)  
  
-   [<span data-ttu-id="cee07-114">Zařazování varianty ByRef</span><span class="sxs-lookup"><span data-stu-id="cee07-114">Marshaling ByRef Variants</span></span>](#cpcondefaultmarshalingforobjectsanchor6)  
  
<a name="cpcondefaultmarshalingforobjectsanchor7"></a>   
## <a name="marshaling-options"></a><span data-ttu-id="cee07-115">Zařazování možnosti</span><span class="sxs-lookup"><span data-stu-id="cee07-115">Marshaling Options</span></span>  
 <span data-ttu-id="cee07-116">V následující tabulce jsou uvedeny možnosti zařazování pro **objekt** datového typu.</span><span class="sxs-lookup"><span data-stu-id="cee07-116">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="cee07-117"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> na objekty zařazování hodnot výčtu.</span><span class="sxs-lookup"><span data-stu-id="cee07-117">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>  
  
|<span data-ttu-id="cee07-118">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="cee07-118">Enumeration type</span></span>|<span data-ttu-id="cee07-119">Popis nespravované formátu</span><span class="sxs-lookup"><span data-stu-id="cee07-119">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="cee07-120">**UnmanagedType.Struct**</span><span class="sxs-lookup"><span data-stu-id="cee07-120">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="cee07-121">(výchozí nastavení pro parametry)</span><span class="sxs-lookup"><span data-stu-id="cee07-121">(default for parameters)</span></span>|<span data-ttu-id="cee07-122">Hodnotu typu variant modelu COM-style.</span><span class="sxs-lookup"><span data-stu-id="cee07-122">A COM-style variant.</span></span>|  
|<span data-ttu-id="cee07-123">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="cee07-123">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="cee07-124">**IDispatch** rozhraní, pokud je to možné, jinak **IUnknown** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cee07-124">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|  
|<span data-ttu-id="cee07-125">**UnmanagedType.IUnknown**</span><span class="sxs-lookup"><span data-stu-id="cee07-125">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="cee07-126">(výchozí nastavení pro pole)</span><span class="sxs-lookup"><span data-stu-id="cee07-126">(default for fields)</span></span>|<span data-ttu-id="cee07-127">**IUnknown** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cee07-127">An **IUnknown** interface.</span></span>|  
|<span data-ttu-id="cee07-128">**UnmanagedType.IDispatch**</span><span class="sxs-lookup"><span data-stu-id="cee07-128">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="cee07-129">**IDispatch** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cee07-129">An **IDispatch** interface.</span></span>|  
  
 <span data-ttu-id="cee07-130">Následující příklad ukazuje použití spravovaného rozhraní definice `MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="cee07-130">The following example shows the managed interface definition for `MarshalObject`.</span></span>  
  
```vb  
Interface MarshalObject  
   Sub SetVariant(o As Object)  
   Sub SetVariantRef(ByRef o As Object)  
   Function GetVariant() As Object  
  
   Sub SetIDispatch( <MarshalAs(UnmanagedType.IDispatch)> o As Object)  
   Sub SetIDispatchRef(ByRef <MarshalAs(UnmanagedType.IDispatch)> o _  
      As Object)  
   Function GetIDispatch() As <MarshalAs(UnmanagedType.IDispatch)> Object  
   Sub SetIUnknown( <MarshalAs(UnmanagedType.IUnknown)> o As Object)  
   Sub SetIUnknownRef(ByRef <MarshalAs(UnmanagedType.IUnknown)> o _  
      As Object)  
   Function GetIUnknown() As <MarshalAs(UnmanagedType.IUnknown)> Object  
End Interface  
```  
  
```csharp  
interface MarshalObject {  
   void SetVariant(Object o);  
   void SetVariantRef(ref Object o);  
   Object GetVariant();  
  
   void SetIDispatch ([MarshalAs(UnmanagedType.IDispatch)]Object o);  
   void SetIDispatchRef([MarshalAs(UnmanagedType.IDispatch)]ref Object o);  
   [MarshalAs(UnmanagedType.IDispatch)] Object GetIDispatch();  
   void SetIUnknown ([MarshalAs(UnmanagedType.IUnknown)]Object o);  
   void SetIUnknownRef([MarshalAs(UnmanagedType.IUnknown)]ref Object o);  
   [MarshalAs(UnmanagedType.IUnknown)] Object GetIUnknown();  
}  
```  
  
 <span data-ttu-id="cee07-131">Následující kód exporty `MarshalObject` rozhraní do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="cee07-131">The following code exports the `MarshalObject` interface to a type library.</span></span>  
  
```  
interface MarshalObject {  
   HRESULT SetVariant([in] VARIANT o);  
   HRESULT SetVariantRef([in,out] VARIANT *o);  
   HRESULT GetVariant([out,retval] VARIANT *o)   
   HRESULT SetIDispatch([in] IDispatch *o);  
   HRESULT SetIDispatchRef([in,out] IDispatch **o);  
   HRESULT GetIDispatch([out,retval] IDispatch **o)   
   HRESULT SetIUnknown([in] IUnknown *o);  
   HRESULT SetIUnknownRef([in,out] IUnknown **o);  
   HRESULT GetIUnknown([out,retval] IUnknown **o)   
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="cee07-132">Interoperační zařazovač automaticky uvolní všechny přidělené objektu uvnitř varianty po volání.</span><span class="sxs-lookup"><span data-stu-id="cee07-132">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>  
  
 <span data-ttu-id="cee07-133">Následující příklad ukazuje typ formátovaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="cee07-133">The following example shows a formatted value type.</span></span>  
  
```vb  
Public Structure ObjectHolder  
   Dim o1 As Object  
   <MarshalAs(UnmanagedType.IDispatch)> Public o2 As Object  
End Structure  
```  
  
```csharp  
public struct ObjectHolder {  
   Object o1;  
   [MarshalAs(UnmanagedType.IDispatch)]public Object o2;  
}  
```  
  
 <span data-ttu-id="cee07-134">Následující kód exportuje typ formátovaný do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="cee07-134">The following code exports the formatted type to a type library.</span></span>  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
<a name="cpcondefaultmarshalingforobjectsanchor2"></a>   
## <a name="marshaling-object-to-interface"></a><span data-ttu-id="cee07-135">Zařazování objektu rozhraní</span><span class="sxs-lookup"><span data-stu-id="cee07-135">Marshaling Object to Interface</span></span>  
 <span data-ttu-id="cee07-136">Pokud objekt je vystavit rozhraní COM jako rozhraní, toto rozhraní je rozhraní pro spravovaný typ <xref:System.Object> ( **d_ostupné** rozhraní).</span><span class="sxs-lookup"><span data-stu-id="cee07-136">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="cee07-137">Toto rozhraní je zadán jako **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) nebo **IUnknown** (**UnmanagedType.IUnknown**) v výslednou knihovnu typů.</span><span class="sxs-lookup"><span data-stu-id="cee07-137">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="cee07-138">Klienti modelu COM může vyvolat dynamicky členy spravovanou třídu nebo všechny členy implementovány z příslušných odvozených tříd prostřednictvím **d_ostupné** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cee07-138">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="cee07-139">Klient může také volat **QueryInterface** získat žádné jiné rozhraní explicitně implementovaných spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="cee07-139">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor3"></a>   
## <a name="marshaling-object-to-variant"></a><span data-ttu-id="cee07-140">Zařazování objektu Variant</span><span class="sxs-lookup"><span data-stu-id="cee07-140">Marshaling Object to Variant</span></span>  
 <span data-ttu-id="cee07-141">Při objektu je zařazení na hodnotu typu variant, interní variantního typu se určuje v době běhu na základě následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="cee07-141">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>  
  
-   <span data-ttu-id="cee07-142">Pokud odkaz na objekt má hodnotu null (**nic** v jazyce Visual Basic), objekt je zařazeno do variant typu **VT_EMPTY**.</span><span class="sxs-lookup"><span data-stu-id="cee07-142">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>  
  
-   <span data-ttu-id="cee07-143">Pokud se objekt instance libovolného typu, které jsou uvedeny v následující tabulce, je výsledný typ variant určeno pravidla součástí zařazování a uvedené v tabulce.</span><span class="sxs-lookup"><span data-stu-id="cee07-143">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>  
  
-   <span data-ttu-id="cee07-144">Můžete implementovat další objekty, které je potřeba explicitně řídit chování zařazování <xref:System.IConvertible> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cee07-144">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="cee07-145">V takovém případě je typ variant určeno kód typu vrácených <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="cee07-145">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cee07-146">V opačném případě je objekt zařazen jako typ variant typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="cee07-146">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>  
  
### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="cee07-147">Zařazování typu Variant typy systémů</span><span class="sxs-lookup"><span data-stu-id="cee07-147">Marshaling System Types to Variant</span></span>  
 <span data-ttu-id="cee07-148">V následující tabulce jsou uvedeny typy spravovaných objektů a jejich odpovídající typy variant modelu COM.</span><span class="sxs-lookup"><span data-stu-id="cee07-148">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="cee07-149">Tyto typy jsou převeden pouze v případě, že podpis volané metody je typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cee07-149">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
|<span data-ttu-id="cee07-150">typ objektu</span><span class="sxs-lookup"><span data-stu-id="cee07-150">Object type</span></span>|<span data-ttu-id="cee07-151">Typ variant modelu COM</span><span class="sxs-lookup"><span data-stu-id="cee07-151">COM variant type</span></span>|  
|-----------------|----------------------|  
|<span data-ttu-id="cee07-152">Odkaz na objekt s hodnotou Null (**nic** v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="cee07-152">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="cee07-153">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="cee07-153">**VT_EMPTY**</span></span>|  
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="cee07-154">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="cee07-154">**VT_NULL**</span></span>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="cee07-155">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="cee07-155">**VT_ERROR**</span></span>|  
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="cee07-156">**VT_ERROR** s **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="cee07-156">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="cee07-157">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="cee07-157">**VT_DISPATCH**</span></span>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="cee07-158">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="cee07-158">**VT_UNKNOWN**</span></span>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="cee07-159">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="cee07-159">**VT_CY**</span></span>|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="cee07-160">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="cee07-160">**VT_BOOL**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="cee07-161">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="cee07-161">**VT_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="cee07-162">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="cee07-162">**VT_UI1**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="cee07-163">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="cee07-163">**VT_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="cee07-164">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="cee07-164">**VT_UI2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="cee07-165">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="cee07-165">**VT_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="cee07-166">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="cee07-166">**VT_UI4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="cee07-167">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="cee07-167">**VT_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="cee07-168">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="cee07-168">**VT_UI8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="cee07-169">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="cee07-169">**VT_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="cee07-170">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="cee07-170">**VT_R8**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="cee07-171">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="cee07-171">**VT_DECIMAL**</span></span>|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="cee07-172">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="cee07-172">**VT_DATE**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="cee07-173">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="cee07-173">**VT_BSTR**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="cee07-174">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="cee07-174">**VT_INT**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="cee07-175">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="cee07-175">**VT_UINT**</span></span>|  
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="cee07-176">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="cee07-176">**VT_ARRAY**</span></span>|  
  
 <span data-ttu-id="cee07-177">Použití `MarshalObject` rozhraní definované v předchozím příkladu následující příklad kódu ukazuje, jak předat různé typy Variant modelu COM serveru.</span><span class="sxs-lookup"><span data-stu-id="cee07-177">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>  
  
```vb  
Dim mo As New MarshalObject()  
mo.SetVariant(Nothing)         ' Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value) ' Marshal as variant of type VT_NULL.  
mo.SetVariant(CInt(27))        ' Marshal as variant of type VT_I2.  
mo.SetVariant(CLng(27))        ' Marshal as variant of type VT_I4.  
mo.SetVariant(CSng(27.0))      ' Marshal as variant of type VT_R4.  
mo.SetVariant(CDbl(27.0))      ' Marshal as variant of type VT_R8.  
```  
  
```csharp  
MarshalObject mo = new MarshalObject();  
mo.SetVariant(null);            // Marshal as variant of type VT_EMPTY.  
mo.SetVariant(System.DBNull.Value); // Marshal as variant of type VT_NULL.  
mo.SetVariant((int)27);          // Marshal as variant of type VT_I2.  
mo.SetVariant((long)27);          // Marshal as variant of type VT_I4.  
mo.SetVariant((single)27.0);   // Marshal as variant of type VT_R4.  
mo.SetVariant((double)27.0);   // Marshal as variant of type VT_R8.  
```  
  
 <span data-ttu-id="cee07-178">Typy modelu COM, které nemají odpovídající spravovaných typů může být zařazována pomocí obálkové třídy, například <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, a <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span><span class="sxs-lookup"><span data-stu-id="cee07-178">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="cee07-179">Následující příklad kódu ukazuje, jak používat tyto obálky pro předávání různých typů variant modelu COM serveru.</span><span class="sxs-lookup"><span data-stu-id="cee07-179">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
' Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(New UnknownWrapper(inew))  
' Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(New DispatchWrapper(inew))  
' Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(New ErrorWrapper(&H80054002))  
' Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(New CurrencyWrapper(New Decimal(5.25)))  
```  
  
```csharp  
using System.Runtime.InteropServices;  
// Pass inew as a variant of type VT_UNKNOWN interface.  
mo.SetVariant(new UnknownWrapper(inew));  
// Pass inew as a variant of type VT_DISPATCH interface.  
mo.SetVariant(new DispatchWrapper(inew));  
// Pass a value as a variant of type VT_ERROR interface.  
mo.SetVariant(new ErrorWrapper(0x80054002));  
// Pass a value as a variant of type VT_CURRENCY interface.  
mo.SetVariant(new CurrencyWrapper(new Decimal(5.25)));  
```  
  
 <span data-ttu-id="cee07-180">Obálkové třídy jsou definovány v <xref:System.Runtime.InteropServices> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cee07-180">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="cee07-181">Zařazování rozhraní IConvertible Variant</span><span class="sxs-lookup"><span data-stu-id="cee07-181">Marshaling the IConvertible Interface to Variant</span></span>  
 <span data-ttu-id="cee07-182">Typy jiné než uvedené v předchozí části můžete řídit, jak jsou zařazeny implementací <xref:System.IConvertible> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cee07-182">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="cee07-183">Pokud objekt implementuje **IConvertible** rozhraní, typ variant modelu COM je stanovena v době běhu hodnotou <xref:System.TypeCode> vrácená z výčtu <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="cee07-183">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="cee07-184">V následující tabulce jsou uvedeny možné hodnoty pro **TypeCode** výčet a odpovídající typ variant modelu COM pro každou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cee07-184">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>  
  
|<span data-ttu-id="cee07-185">TypeCode</span><span class="sxs-lookup"><span data-stu-id="cee07-185">TypeCode</span></span>|<span data-ttu-id="cee07-186">Typ variant modelu COM</span><span class="sxs-lookup"><span data-stu-id="cee07-186">COM variant type</span></span>|  
|--------------|----------------------|  
|<span data-ttu-id="cee07-187">**TypeCode.Empty**</span><span class="sxs-lookup"><span data-stu-id="cee07-187">**TypeCode.Empty**</span></span>|<span data-ttu-id="cee07-188">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="cee07-188">**VT_EMPTY**</span></span>|  
|<span data-ttu-id="cee07-189">**TypeCode.Object**</span><span class="sxs-lookup"><span data-stu-id="cee07-189">**TypeCode.Object**</span></span>|<span data-ttu-id="cee07-190">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="cee07-190">**VT_UNKNOWN**</span></span>|  
|<span data-ttu-id="cee07-191">**TypeCode.DBNull**</span><span class="sxs-lookup"><span data-stu-id="cee07-191">**TypeCode.DBNull**</span></span>|<span data-ttu-id="cee07-192">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="cee07-192">**VT_NULL**</span></span>|  
|<span data-ttu-id="cee07-193">**TypeCode.Boolean**</span><span class="sxs-lookup"><span data-stu-id="cee07-193">**TypeCode.Boolean**</span></span>|<span data-ttu-id="cee07-194">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="cee07-194">**VT_BOOL**</span></span>|  
|<span data-ttu-id="cee07-195">**TypeCode.Char**</span><span class="sxs-lookup"><span data-stu-id="cee07-195">**TypeCode.Char**</span></span>|<span data-ttu-id="cee07-196">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="cee07-196">**VT_UI2**</span></span>|  
|<span data-ttu-id="cee07-197">**TypeCode.Sbyte**</span><span class="sxs-lookup"><span data-stu-id="cee07-197">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="cee07-198">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="cee07-198">**VT_I1**</span></span>|  
|<span data-ttu-id="cee07-199">**TypeCode.Byte**</span><span class="sxs-lookup"><span data-stu-id="cee07-199">**TypeCode.Byte**</span></span>|<span data-ttu-id="cee07-200">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="cee07-200">**VT_UI1**</span></span>|  
|<span data-ttu-id="cee07-201">**TypeCode.Int16**</span><span class="sxs-lookup"><span data-stu-id="cee07-201">**TypeCode.Int16**</span></span>|<span data-ttu-id="cee07-202">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="cee07-202">**VT_I2**</span></span>|  
|<span data-ttu-id="cee07-203">**TypeCode.UInt16**</span><span class="sxs-lookup"><span data-stu-id="cee07-203">**TypeCode.UInt16**</span></span>|<span data-ttu-id="cee07-204">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="cee07-204">**VT_UI2**</span></span>|  
|<span data-ttu-id="cee07-205">**TypeCode.Int32**</span><span class="sxs-lookup"><span data-stu-id="cee07-205">**TypeCode.Int32**</span></span>|<span data-ttu-id="cee07-206">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="cee07-206">**VT_I4**</span></span>|  
|<span data-ttu-id="cee07-207">**TypeCode.UInt32**</span><span class="sxs-lookup"><span data-stu-id="cee07-207">**TypeCode.UInt32**</span></span>|<span data-ttu-id="cee07-208">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="cee07-208">**VT_UI4**</span></span>|  
|<span data-ttu-id="cee07-209">**TypeCode.Int64**</span><span class="sxs-lookup"><span data-stu-id="cee07-209">**TypeCode.Int64**</span></span>|<span data-ttu-id="cee07-210">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="cee07-210">**VT_I8**</span></span>|  
|<span data-ttu-id="cee07-211">**TypeCode.UInt64**</span><span class="sxs-lookup"><span data-stu-id="cee07-211">**TypeCode.UInt64**</span></span>|<span data-ttu-id="cee07-212">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="cee07-212">**VT_UI8**</span></span>|  
|<span data-ttu-id="cee07-213">**TypeCode.Single**</span><span class="sxs-lookup"><span data-stu-id="cee07-213">**TypeCode.Single**</span></span>|<span data-ttu-id="cee07-214">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="cee07-214">**VT_R4**</span></span>|  
|<span data-ttu-id="cee07-215">**TypeCode.Double**</span><span class="sxs-lookup"><span data-stu-id="cee07-215">**TypeCode.Double**</span></span>|<span data-ttu-id="cee07-216">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="cee07-216">**VT_R8**</span></span>|  
|<span data-ttu-id="cee07-217">**TypeCode.Decimal**</span><span class="sxs-lookup"><span data-stu-id="cee07-217">**TypeCode.Decimal**</span></span>|<span data-ttu-id="cee07-218">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="cee07-218">**VT_DECIMAL**</span></span>|  
|<span data-ttu-id="cee07-219">**TypeCode.DateTime**</span><span class="sxs-lookup"><span data-stu-id="cee07-219">**TypeCode.DateTime**</span></span>|<span data-ttu-id="cee07-220">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="cee07-220">**VT_DATE**</span></span>|  
|<span data-ttu-id="cee07-221">**TypeCode.String**</span><span class="sxs-lookup"><span data-stu-id="cee07-221">**TypeCode.String**</span></span>|<span data-ttu-id="cee07-222">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="cee07-222">**VT_BSTR**</span></span>|  
|<span data-ttu-id="cee07-223">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cee07-223">Not supported.</span></span>|<span data-ttu-id="cee07-224">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="cee07-224">**VT_INT**</span></span>|  
|<span data-ttu-id="cee07-225">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cee07-225">Not supported.</span></span>|<span data-ttu-id="cee07-226">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="cee07-226">**VT_UINT**</span></span>|  
|<span data-ttu-id="cee07-227">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cee07-227">Not supported.</span></span>|<span data-ttu-id="cee07-228">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="cee07-228">**VT_ARRAY**</span></span>|  
|<span data-ttu-id="cee07-229">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cee07-229">Not supported.</span></span>|<span data-ttu-id="cee07-230">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="cee07-230">**VT_RECORD**</span></span>|  
|<span data-ttu-id="cee07-231">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cee07-231">Not supported.</span></span>|<span data-ttu-id="cee07-232">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="cee07-232">**VT_CY**</span></span>|  
|<span data-ttu-id="cee07-233">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cee07-233">Not supported.</span></span>|<span data-ttu-id="cee07-234">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="cee07-234">**VT_VARIANT**</span></span>|  
  
 <span data-ttu-id="cee07-235">Hodnota variant modelu COM je určena voláním **IConvertible.To** *typ* rozhraní, ve kterém **k** *typ* je převod rutiny, která odpovídá typu, který byl vrácen z **IConvertible.GetTypeCode**.</span><span class="sxs-lookup"><span data-stu-id="cee07-235">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="cee07-236">Například objekt, který vrátí **TypeCode.Double** z **IConvertible.GetTypeCode** zařazena jako hodnotu typu variant modelu COM typu **VT_R8**.</span><span class="sxs-lookup"><span data-stu-id="cee07-236">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="cee07-237">Můžete získat hodnotu objektu variant (uložené v **dblVal** pole z variant modelu COM) pomocí přetypování na **IConvertible** rozhraní a volání <xref:System.IConvertible.ToDouble%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="cee07-237">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor4"></a>   
## <a name="marshaling-variant-to-object"></a><span data-ttu-id="cee07-238">Zařazování typu Variant pro objekt</span><span class="sxs-lookup"><span data-stu-id="cee07-238">Marshaling Variant to Object</span></span>  
 <span data-ttu-id="cee07-239">Při zařazování typu variant pro objekt, typ a někdy hodnota zařazené varianty Určuje typ objektu vytvořený.</span><span class="sxs-lookup"><span data-stu-id="cee07-239">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="cee07-240">V následující tabulce jsou uvedeny každý typ variant a odpovídající typ objektu, který vytváří zařazování při hodnotu typu variant je předán z modelu COM pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cee07-240">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>  
  
|<span data-ttu-id="cee07-241">Typ variant modelu COM</span><span class="sxs-lookup"><span data-stu-id="cee07-241">COM variant type</span></span>|<span data-ttu-id="cee07-242">typ objektu</span><span class="sxs-lookup"><span data-stu-id="cee07-242">Object type</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="cee07-243">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="cee07-243">**VT_EMPTY**</span></span>|<span data-ttu-id="cee07-244">Odkaz na objekt s hodnotou Null (**nic** v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="cee07-244">Null object reference (**Nothing** in Visual Basic).</span></span>|  
|<span data-ttu-id="cee07-245">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="cee07-245">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-246">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="cee07-246">**VT_DISPATCH**</span></span>|<span data-ttu-id="cee07-247">**System.__ComObject** nebo hodnota null, pokud (pdispVal == null)</span><span class="sxs-lookup"><span data-stu-id="cee07-247">**System.__ComObject** or null if (pdispVal == null)</span></span>|  
|<span data-ttu-id="cee07-248">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="cee07-248">**VT_UNKNOWN**</span></span>|<span data-ttu-id="cee07-249">**System.__ComObject** nebo hodnota null, pokud (punkVal == null)</span><span class="sxs-lookup"><span data-stu-id="cee07-249">**System.__ComObject** or null if (punkVal == null)</span></span>|  
|<span data-ttu-id="cee07-250">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="cee07-250">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-251">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="cee07-251">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-252">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="cee07-252">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-253">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="cee07-253">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-254">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="cee07-254">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-255">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="cee07-255">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-256">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="cee07-256">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-257">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="cee07-257">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-258">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="cee07-258">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-259">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="cee07-259">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-260">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="cee07-260">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-261">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="cee07-261">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-262">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="cee07-262">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-263">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="cee07-263">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-264">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="cee07-264">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-265">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="cee07-265">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-266">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="cee07-266">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-267">**VT_ARRAY** &#124; **VT_**\*</span><span class="sxs-lookup"><span data-stu-id="cee07-267">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-268">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="cee07-268">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="cee07-269">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="cee07-269">**VT_RECORD**</span></span>|<span data-ttu-id="cee07-270">Odpovídající zabalený typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cee07-270">Corresponding boxed value type.</span></span>|  
|<span data-ttu-id="cee07-271">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="cee07-271">**VT_VARIANT**</span></span>|<span data-ttu-id="cee07-272">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cee07-272">Not supported.</span></span>|  
  
 <span data-ttu-id="cee07-273">Variantních typů předávaného z modelu COM pro spravovaný kód a pak zpátky do modelu COM nemusí uchovávat stejný typ variant po dobu trvání volání.</span><span class="sxs-lookup"><span data-stu-id="cee07-273">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="cee07-274">Zvažte, co se stane, když variant typu **VT_DISPATCH** je předán z modelu COM pro rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cee07-274">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="cee07-275">Při zařazování, varianty převést na <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cee07-275">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cee07-276">Pokud **objekt** je pak předán zpět do modelu COM, je zařazené zpět na hodnotu typu variant typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="cee07-276">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="cee07-277">Není zaručeno, že typ variant vytvořen, pokud objekt je zařazení ze spravovaného kódu na COM bude stejného typu jako typ variant původně použitý k vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="cee07-277">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor6"></a>   
## <a name="marshaling-byref-variants"></a><span data-ttu-id="cee07-278">Zařazování varianty ByRef</span><span class="sxs-lookup"><span data-stu-id="cee07-278">Marshaling ByRef Variants</span></span>  
 <span data-ttu-id="cee07-279">I když varianty sami mohou být předány podle hodnoty nebo podle odkazu, **VT_BYREF** příznak můžete také použít s žádným typem variant k označení, že se obsah objektu variant předávají odkazem místo podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cee07-279">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="cee07-280">Rozdíl mezi zařazování varianty podle odkazu a zařazování variantpro s **VT_BYREF** nastaven příznak může být matoucí.</span><span class="sxs-lookup"><span data-stu-id="cee07-280">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="cee07-281">Na následujícím obrázku vysvětluje rozdíly.</span><span class="sxs-lookup"><span data-stu-id="cee07-281">The following illustration clarifies the differences.</span></span>  
  
 <span data-ttu-id="cee07-282">![Typ Variant předány do zásobníku](./media/interopvariant.gif "interopvariant")</span><span class="sxs-lookup"><span data-stu-id="cee07-282">![Variant passed on the stack](./media/interopvariant.gif "interopvariant")</span></span>  
<span data-ttu-id="cee07-283">Varianty předán podle hodnoty a podle reference</span><span class="sxs-lookup"><span data-stu-id="cee07-283">Variants passed by value and by reference</span></span>  
  
 <span data-ttu-id="cee07-284">**Výchozí chování zařazování objektů a proměnných typu Variant podle hodnoty**</span><span class="sxs-lookup"><span data-stu-id="cee07-284">**Default behavior for marshaling objects and variants by value**</span></span>  
  
-   <span data-ttu-id="cee07-285">Při předávání objektů modelu COM ze spravovaného kódu, obsah objektu se zkopíruje do novou variantu vytvořili zařazováním použitím z pravidel definovaných v [zařazování objektu Variant](#cpcondefaultmarshalingforobjectsanchor3).</span><span class="sxs-lookup"><span data-stu-id="cee07-285">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#cpcondefaultmarshalingforobjectsanchor3).</span></span> <span data-ttu-id="cee07-286">Změny provedené v variant v nespravované oblasti nejsou šířeny zpět do původního objektu při návratu z volání.</span><span class="sxs-lookup"><span data-stu-id="cee07-286">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>  
  
-   <span data-ttu-id="cee07-287">Při předání proměnných typu Variant z modelu COM pro spravovaný kód, obsah objektu variant zkopírují do nově vytvořeného objektu pomocí pravidel definovaných v [zařazování typu Variant pro objekt](#cpcondefaultmarshalingforobjectsanchor4).</span><span class="sxs-lookup"><span data-stu-id="cee07-287">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#cpcondefaultmarshalingforobjectsanchor4).</span></span> <span data-ttu-id="cee07-288">Změny provedené v objektu na spravované straně nejsou šířeny zpět do původní typ variant při návratu z volání.</span><span class="sxs-lookup"><span data-stu-id="cee07-288">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>  
  
 <span data-ttu-id="cee07-289">**Výchozí chování zařazování objektů a proměnných typu Variant odkazem.**</span><span class="sxs-lookup"><span data-stu-id="cee07-289">**Default behavior for marshaling objects and variants by reference**</span></span>  
  
 <span data-ttu-id="cee07-290">Šíření změny zpět do volajícího, musí být parametry předány podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="cee07-290">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="cee07-291">Například můžete použít **ref** – klíčové slovo v C# (nebo **ByRef** v jazyce Visual Basic spravovaného kódu) pro předání parametrů podle odkazu.</span><span class="sxs-lookup"><span data-stu-id="cee07-291">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="cee07-292">V modelu COM, odkaz parametry se jí předávají pomocí ukazatele, jako třeba **variant \***.</span><span class="sxs-lookup"><span data-stu-id="cee07-292">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>  
  
-   <span data-ttu-id="cee07-293">Při předávání objektů modelu COM pomocí odkazu, aby zařazování odvozovalo vytvoří novou variantu a zkopíruje obsah odkaz na objekt do varianty předtím, než se provádí volání.</span><span class="sxs-lookup"><span data-stu-id="cee07-293">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="cee07-294">Varianty je předán nespravované funkci, kde uživatel je zdarma pro změnu obsahu objektu variant.</span><span class="sxs-lookup"><span data-stu-id="cee07-294">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="cee07-295">Při návratu z volání všechny změny provedené v nespravované oblasti varianty jsou šířeny zpět na původní objekt.</span><span class="sxs-lookup"><span data-stu-id="cee07-295">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="cee07-296">Pokud se typ objektu variant liší od typu variant předává do volání, změny jsou šířeny zpět do objektu jiného typu.</span><span class="sxs-lookup"><span data-stu-id="cee07-296">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="cee07-297">To znamená typ objektu předaný do volání se může lišit od typu objektu vrácená z volání.</span><span class="sxs-lookup"><span data-stu-id="cee07-297">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>  
  
-   <span data-ttu-id="cee07-298">Při předávání hodnotu typu variant na spravovaný kód podle odkazu, aby zařazování odvozovalo vytvoří nový objekt a zkopíruje obsah objektu variant do objektu před uskutečněním hovoru.</span><span class="sxs-lookup"><span data-stu-id="cee07-298">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="cee07-299">Odkaz na objekt je předán spravované funkce, kde uživatel je zdarma, chcete-li změnit objekt.</span><span class="sxs-lookup"><span data-stu-id="cee07-299">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="cee07-300">Při návratu z volání jsou všechny změny provedené odkazovaný objekt šířeny zpět do původní typ variant.</span><span class="sxs-lookup"><span data-stu-id="cee07-300">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="cee07-301">Pokud typ objektu se liší od typu objektu předaného do volání, změnit typ původní typ variant a hodnota se šíří zpět do variantu.</span><span class="sxs-lookup"><span data-stu-id="cee07-301">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="cee07-302">Znovu typ objektu variant předaná do volání se může lišit od typu hodnota variant vrácená z volání.</span><span class="sxs-lookup"><span data-stu-id="cee07-302">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>  
  
 <span data-ttu-id="cee07-303">**Výchozí chování zařazování variantpro s příznakem VT_BYREF**</span><span class="sxs-lookup"><span data-stu-id="cee07-303">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>  
  
-   <span data-ttu-id="cee07-304">Může mít hodnotu typu variant předávaný spravovaný kód podle hodnoty **VT_BYREF** nastaven příznak označující, že varianty obsahuje odkaz na místo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cee07-304">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="cee07-305">V takovém případě je varianty stále zařazeno do objektu vzhledem k tomu, že varianta je předáván podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cee07-305">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="cee07-306">Zařazování automaticky přístupů přes ukazatel, obsah objektu variant a zkopíruje se do nově vytvořeného objektu před uskutečněním hovoru.</span><span class="sxs-lookup"><span data-stu-id="cee07-306">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="cee07-307">Objekt je pak předán do spravované funkci. Při návratu z volání však není objekt šířeny zpět do původní typ variant.</span><span class="sxs-lookup"><span data-stu-id="cee07-307">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="cee07-308">Změny provedené na spravovaný objekt se ztratí.</span><span class="sxs-lookup"><span data-stu-id="cee07-308">Changes made to the managed object are lost.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="cee07-309">Neexistuje žádný způsob, jak změnit hodnotu typu variant předán podle hodnoty, i v případě varianty **VT_BYREF** nastaven příznak.</span><span class="sxs-lookup"><span data-stu-id="cee07-309">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>  
  
-   <span data-ttu-id="cee07-310">Hodnotu typu variant předávaný odkazem na spravovaný kód může mít také **VT_BYREF** nastaven příznak označující, že varianty obsahuje odkaz na jiný.</span><span class="sxs-lookup"><span data-stu-id="cee07-310">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="cee07-311">Pokud ano, varianty je zařazeno do **ref** objektu, protože varianty je předáván odkazem.</span><span class="sxs-lookup"><span data-stu-id="cee07-311">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="cee07-312">Zařazování automaticky přístupů přes ukazatel, obsah objektu variant a zkopíruje se do nově vytvořeného objektu před uskutečněním hovoru.</span><span class="sxs-lookup"><span data-stu-id="cee07-312">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="cee07-313">Při návratu z volání hodnotu objektu se šíří zpět k odkazu v rámci původní typ variant pouze v případě, že objekt je stejného typu jako objekt předaný v.</span><span class="sxs-lookup"><span data-stu-id="cee07-313">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="cee07-314">To znamená, šíření nezmění typu variant s **VT_BYREF** nastaven příznak.</span><span class="sxs-lookup"><span data-stu-id="cee07-314">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="cee07-315">Pokud se změní typ objektu v průběhu hovoru, <xref:System.InvalidCastException> dojde k návratu z volání.</span><span class="sxs-lookup"><span data-stu-id="cee07-315">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>  
  
 <span data-ttu-id="cee07-316">Následující tabulka shrnuje pravidla pro šíření variant a objektů.</span><span class="sxs-lookup"><span data-stu-id="cee07-316">The following table summarizes the propagation rules for variants and objects.</span></span>  
  
|<span data-ttu-id="cee07-317">From</span><span class="sxs-lookup"><span data-stu-id="cee07-317">From</span></span>|<span data-ttu-id="cee07-318">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="cee07-318">To</span></span>|<span data-ttu-id="cee07-319">Změny šířeny zpět</span><span class="sxs-lookup"><span data-stu-id="cee07-319">Changes propagated back</span></span>|  
|----------|--------|-----------------------------|  
|<span data-ttu-id="cee07-320">\**Varianty\*\*\*v* </span><span class="sxs-lookup"><span data-stu-id="cee07-320">**Variant**  *v*</span></span>|<span data-ttu-id="cee07-321">\**Objekt\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="cee07-321">**Object**  *o*</span></span>|<span data-ttu-id="cee07-322">Nikdy</span><span class="sxs-lookup"><span data-stu-id="cee07-322">Never</span></span>|  
|<span data-ttu-id="cee07-323">\**Objekt\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="cee07-323">**Object**  *o*</span></span>|<span data-ttu-id="cee07-324">\**Varianty\*\*\*v* </span><span class="sxs-lookup"><span data-stu-id="cee07-324">**Variant**  *v*</span></span>|<span data-ttu-id="cee07-325">Nikdy</span><span class="sxs-lookup"><span data-stu-id="cee07-325">Never</span></span>|  
|<span data-ttu-id="cee07-326">\**Varianty\*\*\*\*\*\*\*\*\*\*pv* </span><span class="sxs-lookup"><span data-stu-id="cee07-326">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="cee07-327">\**Objekt REF\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="cee07-327">**Ref Object**  *o*</span></span>|<span data-ttu-id="cee07-328">Vždy</span><span class="sxs-lookup"><span data-stu-id="cee07-328">Always</span></span>|  
|<span data-ttu-id="cee07-329">\**Objekt REF\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="cee07-329">**Ref object**  *o*</span></span>|<span data-ttu-id="cee07-330">\**Varianty\*\*\*\*\*\*\*\*\*\*pv* </span><span class="sxs-lookup"><span data-stu-id="cee07-330">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="cee07-331">Vždy</span><span class="sxs-lookup"><span data-stu-id="cee07-331">Always</span></span>|  
|<span data-ttu-id="cee07-332">\**Varianty\*\*\*v* **(VT_BYREF** *&#124;* **typ VT_\*)** </span><span class="sxs-lookup"><span data-stu-id="cee07-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="cee07-333">\**Objekt\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="cee07-333">**Object**  *o*</span></span>|<span data-ttu-id="cee07-334">Nikdy</span><span class="sxs-lookup"><span data-stu-id="cee07-334">Never</span></span>|  
|<span data-ttu-id="cee07-335">\**Varianty\*\*\*v* **(VT_BYREF** *&#124;* **typ VT_)** </span><span class="sxs-lookup"><span data-stu-id="cee07-335">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="cee07-336">\**Objekt REF\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="cee07-336">**Ref Object**  *o*</span></span>|<span data-ttu-id="cee07-337">Pouze v případě, že nedošlo ke změně typu.</span><span class="sxs-lookup"><span data-stu-id="cee07-337">Only if the type has not changed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cee07-338">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cee07-338">See also</span></span>
- [<span data-ttu-id="cee07-339">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="cee07-339">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="cee07-340">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="cee07-340">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="cee07-341">[Směrové atributy](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cee07-341">[Directional Attributes](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span></span>
- [<span data-ttu-id="cee07-342">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="cee07-342">Copying and Pinning</span></span>](copying-and-pinning.md)
