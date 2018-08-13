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
ms.openlocfilehash: 94377fb2079689e7b6af2c94fa24ca2214a5c729
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2018
ms.locfileid: "34312180"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="a6538-102">Výchozí zařazování pro objekty</span><span class="sxs-lookup"><span data-stu-id="a6538-102">Default Marshaling for Objects</span></span>
<span data-ttu-id="a6538-103">Parametry a pole zadán jako <xref:System.Object?displayProperty=nameWithType> mohou být zpřístupněny nespravovaného kódu jako jeden z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="a6538-103">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>  
  
-   <span data-ttu-id="a6538-104">Hodnotu typu variant, pokud je objekt parametr.</span><span class="sxs-lookup"><span data-stu-id="a6538-104">A variant when the object is a parameter.</span></span>  
  
-   <span data-ttu-id="a6538-105">Rozhraní, pokud je objekt struktura pole.</span><span class="sxs-lookup"><span data-stu-id="a6538-105">An interface when the object is a structure field.</span></span>  
  
 <span data-ttu-id="a6538-106">Pouze spoluprací COM podporuje zařazování pro typy objektů.</span><span class="sxs-lookup"><span data-stu-id="a6538-106">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="a6538-107">Výchozí chování je zařazování objektů COM variant.</span><span class="sxs-lookup"><span data-stu-id="a6538-107">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="a6538-108">Tato pravidla platí pouze pro typ **objekt** a nevztahují se na silného typu objekty, které jsou odvozeny od **objekt** třídy.</span><span class="sxs-lookup"><span data-stu-id="a6538-108">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>  
  
 <span data-ttu-id="a6538-109">Toto téma obsahuje následující doplňkové informace o zařazování typy objektů:</span><span class="sxs-lookup"><span data-stu-id="a6538-109">This topic provides the following additional information about marshaling object types:</span></span>  
  
-   [<span data-ttu-id="a6538-110">Zařazování možnosti</span><span class="sxs-lookup"><span data-stu-id="a6538-110">Marshaling Options</span></span>](#cpcondefaultmarshalingforobjectsanchor7)  
  
-   [<span data-ttu-id="a6538-111">Zařazování objekt rozhraní</span><span class="sxs-lookup"><span data-stu-id="a6538-111">Marshaling Object to Interface</span></span>](#cpcondefaultmarshalingforobjectsanchor2)  
  
-   [<span data-ttu-id="a6538-112">Export objektu na Variant</span><span class="sxs-lookup"><span data-stu-id="a6538-112">Marshaling Object to Variant</span></span>](#cpcondefaultmarshalingforobjectsanchor3)  
  
-   [<span data-ttu-id="a6538-113">Zařazování Variant objektu</span><span class="sxs-lookup"><span data-stu-id="a6538-113">Marshaling Variant to Object</span></span>](#cpcondefaultmarshalingforobjectsanchor4)  
  
-   [<span data-ttu-id="a6538-114">Zařazování ByRef variant</span><span class="sxs-lookup"><span data-stu-id="a6538-114">Marshaling ByRef Variants</span></span>](#cpcondefaultmarshalingforobjectsanchor6)  
  
<a name="cpcondefaultmarshalingforobjectsanchor7"></a>   
## <a name="marshaling-options"></a><span data-ttu-id="a6538-115">Zařazování možnosti</span><span class="sxs-lookup"><span data-stu-id="a6538-115">Marshaling Options</span></span>  
 <span data-ttu-id="a6538-116">Následující tabulka uvádí možnosti zařazování **objekt** datového typu.</span><span class="sxs-lookup"><span data-stu-id="a6538-116">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="a6538-117"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut nabízí několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnoty výčtu k zařazení objekty.</span><span class="sxs-lookup"><span data-stu-id="a6538-117">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>  
  
|<span data-ttu-id="a6538-118">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="a6538-118">Enumeration type</span></span>|<span data-ttu-id="a6538-119">Popis nespravované formátu</span><span class="sxs-lookup"><span data-stu-id="a6538-119">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="a6538-120">**UnmanagedType.Struct**</span><span class="sxs-lookup"><span data-stu-id="a6538-120">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="a6538-121">(výchozí nastavení pro parametry)</span><span class="sxs-lookup"><span data-stu-id="a6538-121">(default for parameters)</span></span>|<span data-ttu-id="a6538-122">Hodnotu typu variant COM stylu.</span><span class="sxs-lookup"><span data-stu-id="a6538-122">A COM-style variant.</span></span>|  
|<span data-ttu-id="a6538-123">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="a6538-123">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="a6538-124">**IDispatch** rozhraní, pokud je to možné; jinak **IUnknown** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a6538-124">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|  
|<span data-ttu-id="a6538-125">**UnmanagedType.IUnknown**</span><span class="sxs-lookup"><span data-stu-id="a6538-125">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="a6538-126">(výchozí nastavení pro pole)</span><span class="sxs-lookup"><span data-stu-id="a6538-126">(default for fields)</span></span>|<span data-ttu-id="a6538-127">**IUnknown** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a6538-127">An **IUnknown** interface.</span></span>|  
|<span data-ttu-id="a6538-128">**UnmanagedType.IDispatch**</span><span class="sxs-lookup"><span data-stu-id="a6538-128">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="a6538-129">**IDispatch** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a6538-129">An **IDispatch** interface.</span></span>|  
  
 <span data-ttu-id="a6538-130">Následující příklad ukazuje definici spravovaného rozhraní `MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="a6538-130">The following example shows the managed interface definition for `MarshalObject`.</span></span>  
  
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
  
 <span data-ttu-id="a6538-131">Následující kód exportuje `MarshalObject` rozhraní pro knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="a6538-131">The following code exports the `MarshalObject` interface to a type library.</span></span>  
  
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
>  <span data-ttu-id="a6538-132">Spolupráce vláken automaticky uvolní všechny přidělené objekt uvnitř varianta po volání.</span><span class="sxs-lookup"><span data-stu-id="a6538-132">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>  
  
 <span data-ttu-id="a6538-133">Následující příklad ukazuje typ formátovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a6538-133">The following example shows a formatted value type.</span></span>  
  
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
  
 <span data-ttu-id="a6538-134">Následující kód exportuje formátovaný typ do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="a6538-134">The following code exports the formatted type to a type library.</span></span>  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
<a name="cpcondefaultmarshalingforobjectsanchor2"></a>   
## <a name="marshaling-object-to-interface"></a><span data-ttu-id="a6538-135">Zařazování objekt rozhraní</span><span class="sxs-lookup"><span data-stu-id="a6538-135">Marshaling Object to Interface</span></span>  
 <span data-ttu-id="a6538-136">Pokud objekt je vystaven objektům modelu COM jako rozhraní, tento rozhraní je třída rozhraní pro spravovaný typ <xref:System.Object> ( **_Object** rozhraní).</span><span class="sxs-lookup"><span data-stu-id="a6538-136">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="a6538-137">Toto rozhraní je zadán jako **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) nebo **IUnknown** (**UnmanagedType.IUnknown**) v knihovně výsledný typ.</span><span class="sxs-lookup"><span data-stu-id="a6538-137">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="a6538-138">Klienti COM můžete vyvolat dynamicky členy spravované třídy nebo žádné členy implementované jejich odvozené třídy prostřednictvím **_Object** rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a6538-138">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="a6538-139">Klient může také volat **QueryInterface** získat všechny rozhraní, které explicitně implementované spravovaného typu.</span><span class="sxs-lookup"><span data-stu-id="a6538-139">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor3"></a>   
## <a name="marshaling-object-to-variant"></a><span data-ttu-id="a6538-140">Export objektu na Variant</span><span class="sxs-lookup"><span data-stu-id="a6538-140">Marshaling Object to Variant</span></span>  
 <span data-ttu-id="a6538-141">Pokud je objekt zařazen do hodnotu typu variant, interní typ varianty se určuje v době běhu na základě následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="a6538-141">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>  
  
-   <span data-ttu-id="a6538-142">Pokud objekt odkaz má hodnotu null (**nic** v jazyce Visual Basic), objekt je zařazen do hodnotu typu variant typu **VT_EMPTY**.</span><span class="sxs-lookup"><span data-stu-id="a6538-142">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>  
  
-   <span data-ttu-id="a6538-143">Pokud se objekt instance libovolného typu uvedené v následující tabulce, výsledný typ varianty je určen podle pravidel integrovaných do zařazování a uvedené v tabulce.</span><span class="sxs-lookup"><span data-stu-id="a6538-143">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>  
  
-   <span data-ttu-id="a6538-144">Můžete implementovat jiné objekty, které je potřeba explicitně řídit chování zařazování <xref:System.IConvertible> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a6538-144">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="a6538-145">V takovém případě je typ varianty dáno kód typ vrácený <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="a6538-145">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a6538-146">Jinak je objekt zařazené jako typ variant typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="a6538-146">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>  
  
### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="a6538-147">Zařazování typy systémů Variant</span><span class="sxs-lookup"><span data-stu-id="a6538-147">Marshaling System Types to Variant</span></span>  
 <span data-ttu-id="a6538-148">V následující tabulce jsou uvedeny typy spravovaných objektů a jejich odpovídající typy variant COM.</span><span class="sxs-lookup"><span data-stu-id="a6538-148">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="a6538-149">Tyto typy budou převedené jenom v případě, že podpis metody volané je typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6538-149">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
|<span data-ttu-id="a6538-150">typ objektu</span><span class="sxs-lookup"><span data-stu-id="a6538-150">Object type</span></span>|<span data-ttu-id="a6538-151">Typ varianty COM</span><span class="sxs-lookup"><span data-stu-id="a6538-151">COM variant type</span></span>|  
|-----------------|----------------------|  
|<span data-ttu-id="a6538-152">Odkaz na objekt s hodnotou Null (**nic** v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a6538-152">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="a6538-153">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="a6538-153">**VT_EMPTY**</span></span>|  
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="a6538-154">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="a6538-154">**VT_NULL**</span></span>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="a6538-155">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="a6538-155">**VT_ERROR**</span></span>|  
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="a6538-156">**VT_ERROR** s **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="a6538-156">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="a6538-157">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="a6538-157">**VT_DISPATCH**</span></span>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="a6538-158">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="a6538-158">**VT_UNKNOWN**</span></span>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="a6538-159">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="a6538-159">**VT_CY**</span></span>|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="a6538-160">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="a6538-160">**VT_BOOL**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="a6538-161">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="a6538-161">**VT_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="a6538-162">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="a6538-162">**VT_UI1**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="a6538-163">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="a6538-163">**VT_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="a6538-164">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="a6538-164">**VT_UI2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="a6538-165">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="a6538-165">**VT_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="a6538-166">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="a6538-166">**VT_UI4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="a6538-167">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="a6538-167">**VT_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="a6538-168">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="a6538-168">**VT_UI8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="a6538-169">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="a6538-169">**VT_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="a6538-170">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="a6538-170">**VT_R8**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="a6538-171">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="a6538-171">**VT_DECIMAL**</span></span>|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="a6538-172">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="a6538-172">**VT_DATE**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="a6538-173">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="a6538-173">**VT_BSTR**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="a6538-174">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="a6538-174">**VT_INT**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="a6538-175">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="a6538-175">**VT_UINT**</span></span>|  
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="a6538-176">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="a6538-176">**VT_ARRAY**</span></span>|  
  
 <span data-ttu-id="a6538-177">Pomocí `MarshalObject` rozhraní definované v předchozím příkladu následující příklad kódu ukazuje, jak mají být předány různé typy variant COM server.</span><span class="sxs-lookup"><span data-stu-id="a6538-177">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>  
  
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
  
 <span data-ttu-id="a6538-178">Typy modelu COM, které nemají odpovídající spravované typy může být zařazeno pomocí Obálka – třídy, jako třeba <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, a <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span><span class="sxs-lookup"><span data-stu-id="a6538-178">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="a6538-179">Následující příklad kódu ukazuje, jak používat tyto obálky předat různé typy variant COM server.</span><span class="sxs-lookup"><span data-stu-id="a6538-179">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>  
  
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
  
 <span data-ttu-id="a6538-180">Obálkové třídy jsou definovány v <xref:System.Runtime.InteropServices> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a6538-180">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="a6538-181">Zařazování rozhraní IConvertible Variant</span><span class="sxs-lookup"><span data-stu-id="a6538-181">Marshaling the IConvertible Interface to Variant</span></span>  
 <span data-ttu-id="a6538-182">Typy jiné než jsou uvedeny v předchozí části můžete řídit, jak jsou zařazené implementací <xref:System.IConvertible> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a6538-182">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="a6538-183">Pokud objekt implementuje **IConvertible** rozhraní, typ varianty COM je určen v době běhu hodnotou <xref:System.TypeCode> výčtu vrácená z <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="a6538-183">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a6538-184">V následující tabulce jsou uvedeny možné hodnoty **typ objektu TypeCode** výčet a odpovídající typ varianty COM pro každou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a6538-184">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>  
  
|<span data-ttu-id="a6538-185">Typ objektu TypeCode</span><span class="sxs-lookup"><span data-stu-id="a6538-185">TypeCode</span></span>|<span data-ttu-id="a6538-186">Typ varianty COM</span><span class="sxs-lookup"><span data-stu-id="a6538-186">COM variant type</span></span>|  
|--------------|----------------------|  
|<span data-ttu-id="a6538-187">**TypeCode.Empty**</span><span class="sxs-lookup"><span data-stu-id="a6538-187">**TypeCode.Empty**</span></span>|<span data-ttu-id="a6538-188">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="a6538-188">**VT_EMPTY**</span></span>|  
|<span data-ttu-id="a6538-189">**TypeCode.Object**</span><span class="sxs-lookup"><span data-stu-id="a6538-189">**TypeCode.Object**</span></span>|<span data-ttu-id="a6538-190">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="a6538-190">**VT_UNKNOWN**</span></span>|  
|<span data-ttu-id="a6538-191">**TypeCode.DBNull**</span><span class="sxs-lookup"><span data-stu-id="a6538-191">**TypeCode.DBNull**</span></span>|<span data-ttu-id="a6538-192">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="a6538-192">**VT_NULL**</span></span>|  
|<span data-ttu-id="a6538-193">**TypeCode.Boolean**</span><span class="sxs-lookup"><span data-stu-id="a6538-193">**TypeCode.Boolean**</span></span>|<span data-ttu-id="a6538-194">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="a6538-194">**VT_BOOL**</span></span>|  
|<span data-ttu-id="a6538-195">**TypeCode.Char**</span><span class="sxs-lookup"><span data-stu-id="a6538-195">**TypeCode.Char**</span></span>|<span data-ttu-id="a6538-196">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="a6538-196">**VT_UI2**</span></span>|  
|<span data-ttu-id="a6538-197">**TypeCode.Sbyte**</span><span class="sxs-lookup"><span data-stu-id="a6538-197">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="a6538-198">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="a6538-198">**VT_I1**</span></span>|  
|<span data-ttu-id="a6538-199">**TypeCode.Byte**</span><span class="sxs-lookup"><span data-stu-id="a6538-199">**TypeCode.Byte**</span></span>|<span data-ttu-id="a6538-200">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="a6538-200">**VT_UI1**</span></span>|  
|<span data-ttu-id="a6538-201">**TypeCode.Int16**</span><span class="sxs-lookup"><span data-stu-id="a6538-201">**TypeCode.Int16**</span></span>|<span data-ttu-id="a6538-202">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="a6538-202">**VT_I2**</span></span>|  
|<span data-ttu-id="a6538-203">**TypeCode.UInt16**</span><span class="sxs-lookup"><span data-stu-id="a6538-203">**TypeCode.UInt16**</span></span>|<span data-ttu-id="a6538-204">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="a6538-204">**VT_UI2**</span></span>|  
|<span data-ttu-id="a6538-205">**TypeCode.Int32**</span><span class="sxs-lookup"><span data-stu-id="a6538-205">**TypeCode.Int32**</span></span>|<span data-ttu-id="a6538-206">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="a6538-206">**VT_I4**</span></span>|  
|<span data-ttu-id="a6538-207">**TypeCode.UInt32**</span><span class="sxs-lookup"><span data-stu-id="a6538-207">**TypeCode.UInt32**</span></span>|<span data-ttu-id="a6538-208">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="a6538-208">**VT_UI4**</span></span>|  
|<span data-ttu-id="a6538-209">**TypeCode.Int64**</span><span class="sxs-lookup"><span data-stu-id="a6538-209">**TypeCode.Int64**</span></span>|<span data-ttu-id="a6538-210">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="a6538-210">**VT_I8**</span></span>|  
|<span data-ttu-id="a6538-211">**TypeCode.UInt64**</span><span class="sxs-lookup"><span data-stu-id="a6538-211">**TypeCode.UInt64**</span></span>|<span data-ttu-id="a6538-212">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="a6538-212">**VT_UI8**</span></span>|  
|<span data-ttu-id="a6538-213">**TypeCode.Single**</span><span class="sxs-lookup"><span data-stu-id="a6538-213">**TypeCode.Single**</span></span>|<span data-ttu-id="a6538-214">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="a6538-214">**VT_R4**</span></span>|  
|<span data-ttu-id="a6538-215">**TypeCode.Double**</span><span class="sxs-lookup"><span data-stu-id="a6538-215">**TypeCode.Double**</span></span>|<span data-ttu-id="a6538-216">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="a6538-216">**VT_R8**</span></span>|  
|<span data-ttu-id="a6538-217">**TypeCode.Decimal**</span><span class="sxs-lookup"><span data-stu-id="a6538-217">**TypeCode.Decimal**</span></span>|<span data-ttu-id="a6538-218">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="a6538-218">**VT_DECIMAL**</span></span>|  
|<span data-ttu-id="a6538-219">**TypeCode.DateTime**</span><span class="sxs-lookup"><span data-stu-id="a6538-219">**TypeCode.DateTime**</span></span>|<span data-ttu-id="a6538-220">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="a6538-220">**VT_DATE**</span></span>|  
|<span data-ttu-id="a6538-221">**TypeCode.String**</span><span class="sxs-lookup"><span data-stu-id="a6538-221">**TypeCode.String**</span></span>|<span data-ttu-id="a6538-222">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="a6538-222">**VT_BSTR**</span></span>|  
|<span data-ttu-id="a6538-223">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="a6538-223">Not supported.</span></span>|<span data-ttu-id="a6538-224">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="a6538-224">**VT_INT**</span></span>|  
|<span data-ttu-id="a6538-225">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="a6538-225">Not supported.</span></span>|<span data-ttu-id="a6538-226">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="a6538-226">**VT_UINT**</span></span>|  
|<span data-ttu-id="a6538-227">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="a6538-227">Not supported.</span></span>|<span data-ttu-id="a6538-228">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="a6538-228">**VT_ARRAY**</span></span>|  
|<span data-ttu-id="a6538-229">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="a6538-229">Not supported.</span></span>|<span data-ttu-id="a6538-230">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="a6538-230">**VT_RECORD**</span></span>|  
|<span data-ttu-id="a6538-231">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="a6538-231">Not supported.</span></span>|<span data-ttu-id="a6538-232">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="a6538-232">**VT_CY**</span></span>|  
|<span data-ttu-id="a6538-233">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="a6538-233">Not supported.</span></span>|<span data-ttu-id="a6538-234">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="a6538-234">**VT_VARIANT**</span></span>|  
  
 <span data-ttu-id="a6538-235">Hodnotu typu variant COM je dáno volání **IConvertible.To** *typ* rozhraní, kde **k** *typu* je převod rutiny, která odpovídá typu, který byl vrácen ze **IConvertible.GetTypeCode**.</span><span class="sxs-lookup"><span data-stu-id="a6538-235">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="a6538-236">Například objekt, který vrátí **TypeCode.Double** z **IConvertible.GetTypeCode** je zařazené jako hodnotu typu variant COM typu **VT_R8**.</span><span class="sxs-lookup"><span data-stu-id="a6538-236">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="a6538-237">Můžete získat hodnotu varianta (uložené v **dblVal** pole varianty COM) podle přetypování k **IConvertible** rozhraní a volání <xref:System.IConvertible.ToDouble%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="a6538-237">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor4"></a>   
## <a name="marshaling-variant-to-object"></a><span data-ttu-id="a6538-238">Zařazování Variant objektu</span><span class="sxs-lookup"><span data-stu-id="a6538-238">Marshaling Variant to Object</span></span>  
 <span data-ttu-id="a6538-239">Při zařazování hodnotu typu variant pro objekt, typ a někdy hodnotu zařazené variant Určuje typ objektu vytvořil.</span><span class="sxs-lookup"><span data-stu-id="a6538-239">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="a6538-240">V následující tabulce jsou uvedeny každý typ varianty a odpovídající typ objektu, který zařazování vytvoří, když hodnotu typu variant předána z COM rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6538-240">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>  
  
|<span data-ttu-id="a6538-241">Typ varianty COM</span><span class="sxs-lookup"><span data-stu-id="a6538-241">COM variant type</span></span>|<span data-ttu-id="a6538-242">typ objektu</span><span class="sxs-lookup"><span data-stu-id="a6538-242">Object type</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="a6538-243">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="a6538-243">**VT_EMPTY**</span></span>|<span data-ttu-id="a6538-244">Odkaz na objekt s hodnotou Null (**nic** v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a6538-244">Null object reference (**Nothing** in Visual Basic).</span></span>|  
|<span data-ttu-id="a6538-245">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="a6538-245">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-246">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="a6538-246">**VT_DISPATCH**</span></span>|<span data-ttu-id="a6538-247">**System.__ComObject** nebo hodnota null, pokud (pdispVal == null)</span><span class="sxs-lookup"><span data-stu-id="a6538-247">**System.__ComObject** or null if (pdispVal == null)</span></span>|  
|<span data-ttu-id="a6538-248">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="a6538-248">**VT_UNKNOWN**</span></span>|<span data-ttu-id="a6538-249">**System.__ComObject** nebo hodnota null, pokud (punkVal == null)</span><span class="sxs-lookup"><span data-stu-id="a6538-249">**System.__ComObject** or null if (punkVal == null)</span></span>|  
|<span data-ttu-id="a6538-250">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="a6538-250">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-251">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="a6538-251">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-252">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="a6538-252">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-253">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="a6538-253">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-254">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="a6538-254">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-255">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="a6538-255">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-256">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="a6538-256">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-257">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="a6538-257">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-258">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="a6538-258">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-259">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="a6538-259">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-260">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="a6538-260">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-261">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="a6538-261">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-262">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="a6538-262">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-263">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="a6538-263">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-264">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="a6538-264">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-265">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="a6538-265">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-266">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="a6538-266">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-267">**VT_ARRAY** &#124; **VT_**\*</span><span class="sxs-lookup"><span data-stu-id="a6538-267">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-268">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="a6538-268">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="a6538-269">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="a6538-269">**VT_RECORD**</span></span>|<span data-ttu-id="a6538-270">Odpovídající typ zabalené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a6538-270">Corresponding boxed value type.</span></span>|  
|<span data-ttu-id="a6538-271">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="a6538-271">**VT_VARIANT**</span></span>|<span data-ttu-id="a6538-272">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="a6538-272">Not supported.</span></span>|  
  
 <span data-ttu-id="a6538-273">Variant typy předat z COM pro spravovaný kód a potom zpět do modelu COM nemusí zachovat stejný typ varianty po dobu trvání volání.</span><span class="sxs-lookup"><span data-stu-id="a6538-273">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="a6538-274">Zvažte, co se stane, když hodnotu typu variant typu **VT_DISPATCH** předaný z COM rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6538-274">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="a6538-275">Při zařazování, varianta jsou převedeny na <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a6538-275">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a6538-276">Pokud **objekt** byl následně předán zpět do modelu COM, je zařazené zpět na hodnotu typu variant typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="a6538-276">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="a6538-277">Není zaručeno, že bude variant vytváří, když je objekt zařazené ze spravovaného kódu do modelu COM stejného typu jako typ variant původně použitý k vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="a6538-277">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor6"></a>   
## <a name="marshaling-byref-variants"></a><span data-ttu-id="a6538-278">Zařazování ByRef variant</span><span class="sxs-lookup"><span data-stu-id="a6538-278">Marshaling ByRef Variants</span></span>  
 <span data-ttu-id="a6538-279">I když hodnotou nebo odkazem, se dá předat variant sami **VT_BYREF** příznak lze také s žádným typem variant indikující, že obsah varianta jsou předávány odkazem místo podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a6538-279">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="a6538-280">Rozdíl mezi zařazování variant odkazem a zařazování hodnotu typu variant s **VT_BYREF** nastaven příznak může být matoucí.</span><span class="sxs-lookup"><span data-stu-id="a6538-280">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="a6538-281">Na následujícím obrázku vysvětluje rozdíly.</span><span class="sxs-lookup"><span data-stu-id="a6538-281">The following illustration clarifies the differences.</span></span>  
  
 <span data-ttu-id="a6538-282">![Variant předán v zásobníku](./media/interopvariant.gif "interopvariant")</span><span class="sxs-lookup"><span data-stu-id="a6538-282">![Variant passed on the stack](./media/interopvariant.gif "interopvariant")</span></span>  
<span data-ttu-id="a6538-283">Variant předán podle hodnoty a podle reference</span><span class="sxs-lookup"><span data-stu-id="a6538-283">Variants passed by value and by reference</span></span>  
  
 <span data-ttu-id="a6538-284">**Výchozí chování zařazování objekty a variant podle hodnoty**</span><span class="sxs-lookup"><span data-stu-id="a6538-284">**Default behavior for marshaling objects and variants by value**</span></span>  
  
-   <span data-ttu-id="a6538-285">Při předávání objektů ze spravovaného kódu do modelu COM, obsah objektu se zkopírují do nové varianty vytvořené vláken, pomocí pravidla definovaná v [zařazování objekt typu Variant](#cpcondefaultmarshalingforobjectsanchor3).</span><span class="sxs-lookup"><span data-stu-id="a6538-285">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#cpcondefaultmarshalingforobjectsanchor3).</span></span> <span data-ttu-id="a6538-286">Změny provedené v typu variant na nespravované straně nebudou rozšířeny zpět na původní objekt pro návrat z volání.</span><span class="sxs-lookup"><span data-stu-id="a6538-286">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>  
  
-   <span data-ttu-id="a6538-287">Při předávání variant do spravovaného kódu z modelu COM, obsah varianty se zkopíruje na nově vytvořený objekt, pomocí pravidla definovaná v [zařazování Variant objekt](#cpcondefaultmarshalingforobjectsanchor4).</span><span class="sxs-lookup"><span data-stu-id="a6538-287">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#cpcondefaultmarshalingforobjectsanchor4).</span></span> <span data-ttu-id="a6538-288">Změny provedené v objektu na straně pro spravované nebudou rozšířeny zpět na původní typu variant pro návrat z volání.</span><span class="sxs-lookup"><span data-stu-id="a6538-288">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>  
  
 <span data-ttu-id="a6538-289">**Výchozí chování zařazování objekty a variant odkazem**</span><span class="sxs-lookup"><span data-stu-id="a6538-289">**Default behavior for marshaling objects and variants by reference**</span></span>  
  
 <span data-ttu-id="a6538-290">Rozšíří změny zpět do volající, musí být předán parametry odkazem.</span><span class="sxs-lookup"><span data-stu-id="a6538-290">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="a6538-291">Například můžete použít **ref** – klíčové slovo v jazyce C# (nebo **ByRef** v jazyce Visual Basic spravovaný kód) předat parametry odkazem.</span><span class="sxs-lookup"><span data-stu-id="a6538-291">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="a6538-292">V modelu COM, odkaz parametry se jí předávají pomocí ukazatele, jako třeba **variant \***.</span><span class="sxs-lookup"><span data-stu-id="a6538-292">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>  
  
-   <span data-ttu-id="a6538-293">Při předávání objektu COM odkazem, zařazování vytvoří nové typu variant a zkopíruje obsah odkaz na objekt do varianta než při volání.</span><span class="sxs-lookup"><span data-stu-id="a6538-293">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="a6538-294">Varianta předaný funkci nespravované kde je mohou změnit obsah varianta uživatele.</span><span class="sxs-lookup"><span data-stu-id="a6538-294">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="a6538-295">Při návratu z volání všechny změny typu variant na nespravované straně rozšířeny zpět na původní objekt.</span><span class="sxs-lookup"><span data-stu-id="a6538-295">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="a6538-296">Pokud typ varianty se liší od typu variant předána volání funkce, změny rozšířeny zpět do objektu jiného typu.</span><span class="sxs-lookup"><span data-stu-id="a6538-296">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="a6538-297">To znamená typ objektu, který je předán do volání se může lišit od typ objektu vrácená z volání.</span><span class="sxs-lookup"><span data-stu-id="a6538-297">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>  
  
-   <span data-ttu-id="a6538-298">Při předávání hodnotu typu variant pro spravovaný kód podle reference, zařazování vytvoří nový objekt a zkopíruje obsah varianta do objektu před uskutečněním hovoru.</span><span class="sxs-lookup"><span data-stu-id="a6538-298">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="a6538-299">Odkaz na objekt předaný spravovaná funkce, kde je mohou změnit objekt uživatele.</span><span class="sxs-lookup"><span data-stu-id="a6538-299">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="a6538-300">Při návratu z volání všechny změny odkazovaného objektu rozšířeny zpět na původní variant.</span><span class="sxs-lookup"><span data-stu-id="a6538-300">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="a6538-301">Pokud typ objektu, se liší od typ objektu předané do volání, se změní typ původní typu variant a je hodnota rozšířena zpět do varianta.</span><span class="sxs-lookup"><span data-stu-id="a6538-301">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="a6538-302">Znovu typ variant předaný do volání se může lišit od typu variant vrácená z volání.</span><span class="sxs-lookup"><span data-stu-id="a6538-302">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>  
  
 <span data-ttu-id="a6538-303">**Výchozí chování zařazování hodnotu typu variant nastaven příznak VT_BYREF**</span><span class="sxs-lookup"><span data-stu-id="a6538-303">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>  
  
-   <span data-ttu-id="a6538-304">Může mít hodnotu typu variant předávány do spravovaného kódu podle hodnoty **VT_BYREF** nastaven příznak indikující, že varianta obsahuje odkaz místo hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a6538-304">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="a6538-305">V takovém případě je varianta stále zařazené k objektu, protože varianta je předáván podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a6538-305">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="a6538-306">Zařazování automaticky dereferences obsah varianta a zkopíruje je do nově vytvořený objekt před uskutečněním hovoru.</span><span class="sxs-lookup"><span data-stu-id="a6538-306">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="a6538-307">Objekt je předána do spravované funkce; Při návratu z volání, však není objekt rozšíří zpět do původní variant.</span><span class="sxs-lookup"><span data-stu-id="a6538-307">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="a6538-308">Změny spravovaného objektu jsou ztraceny.</span><span class="sxs-lookup"><span data-stu-id="a6538-308">Changes made to the managed object are lost.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="a6538-309">Neexistuje žádný způsob, jak změnit hodnotu typu variant předaná hodnota, i když má varianta **VT_BYREF** nastaven příznak.</span><span class="sxs-lookup"><span data-stu-id="a6538-309">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>  
  
-   <span data-ttu-id="a6538-310">Může mít hodnotu typu variant předávány do spravovaného kódu odkazem **VT_BYREF** nastaven příznak indikující, že varianta obsahuje odkaz na jiný.</span><span class="sxs-lookup"><span data-stu-id="a6538-310">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="a6538-311">Pokud ano, je varianta zařazen do **ref** objekt, protože varianta je předávána odkazem.</span><span class="sxs-lookup"><span data-stu-id="a6538-311">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="a6538-312">Zařazování automaticky dereferences obsah varianta a zkopíruje je do nově vytvořený objekt před uskutečněním hovoru.</span><span class="sxs-lookup"><span data-stu-id="a6538-312">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="a6538-313">Při návratu z volání je hodnota objektu rozšířena zpět na odkaz v původní variant pouze v případě, že objekt je stejného typu jako objekt předaný v.</span><span class="sxs-lookup"><span data-stu-id="a6538-313">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="a6538-314">To znamená, šíření nezmění typ variant s **VT_BYREF** nastaven příznak.</span><span class="sxs-lookup"><span data-stu-id="a6538-314">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="a6538-315">Pokud je během volání změnit typ objektu <xref:System.InvalidCastException> proběhne vrátit z volání.</span><span class="sxs-lookup"><span data-stu-id="a6538-315">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>  
  
 <span data-ttu-id="a6538-316">Následující tabulka shrnuje pravidla šíření variant a objekty.</span><span class="sxs-lookup"><span data-stu-id="a6538-316">The following table summarizes the propagation rules for variants and objects.</span></span>  
  
|<span data-ttu-id="a6538-317">From</span><span class="sxs-lookup"><span data-stu-id="a6538-317">From</span></span>|<span data-ttu-id="a6538-318">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="a6538-318">To</span></span>|<span data-ttu-id="a6538-319">Změny rozšířeny zpět</span><span class="sxs-lookup"><span data-stu-id="a6538-319">Changes propagated back</span></span>|  
|----------|--------|-----------------------------|  
|<span data-ttu-id="a6538-320">**Variant***v*</span><span class="sxs-lookup"><span data-stu-id="a6538-320">**Variant**  *v*</span></span>|<span data-ttu-id="a6538-321">**Objekt***o*</span><span class="sxs-lookup"><span data-stu-id="a6538-321">**Object**  *o*</span></span>|<span data-ttu-id="a6538-322">Nikdy</span><span class="sxs-lookup"><span data-stu-id="a6538-322">Never</span></span>|  
|<span data-ttu-id="a6538-323">**Objekt***o*</span><span class="sxs-lookup"><span data-stu-id="a6538-323">**Object**  *o*</span></span>|<span data-ttu-id="a6538-324">**Variant***v*</span><span class="sxs-lookup"><span data-stu-id="a6538-324">**Variant**  *v*</span></span>|<span data-ttu-id="a6538-325">Nikdy</span><span class="sxs-lookup"><span data-stu-id="a6538-325">Never</span></span>|  
|<span data-ttu-id="a6538-326">\**Variant\*\*\*\*\*\*\*\*\*\*pv*</span><span class="sxs-lookup"><span data-stu-id="a6538-326">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="a6538-327">**REF objekt***o*</span><span class="sxs-lookup"><span data-stu-id="a6538-327">**Ref Object**  *o*</span></span>|<span data-ttu-id="a6538-328">Vždy</span><span class="sxs-lookup"><span data-stu-id="a6538-328">Always</span></span>|  
|<span data-ttu-id="a6538-329">**REF objekt***o*</span><span class="sxs-lookup"><span data-stu-id="a6538-329">**Ref object**  *o*</span></span>|<span data-ttu-id="a6538-330">\**Variant\*\*\*\*\*\*\*\*\*\*pv*</span><span class="sxs-lookup"><span data-stu-id="a6538-330">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="a6538-331">Vždy</span><span class="sxs-lookup"><span data-stu-id="a6538-331">Always</span></span>|  
|<span data-ttu-id="a6538-332">\**Variant\*\*\*v* **(VT_BYREF** *&#124;* **typ VT_\*)**</span><span class="sxs-lookup"><span data-stu-id="a6538-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="a6538-333">**Objekt***o*</span><span class="sxs-lookup"><span data-stu-id="a6538-333">**Object**  *o*</span></span>|<span data-ttu-id="a6538-334">Nikdy</span><span class="sxs-lookup"><span data-stu-id="a6538-334">Never</span></span>|  
|<span data-ttu-id="a6538-335">**Variant***v* **(VT_BYREF** *&#124;* **typ VT_)**</span><span class="sxs-lookup"><span data-stu-id="a6538-335">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="a6538-336">**REF objekt***o*</span><span class="sxs-lookup"><span data-stu-id="a6538-336">**Ref Object**  *o*</span></span>|<span data-ttu-id="a6538-337">Pouze v případě, že typ nebyl změněn.</span><span class="sxs-lookup"><span data-stu-id="a6538-337">Only if the type has not changed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6538-338">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6538-338">See Also</span></span>  
 [<span data-ttu-id="a6538-339">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="a6538-339">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)  
 [<span data-ttu-id="a6538-340">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="a6538-340">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)  
 <span data-ttu-id="a6538-341">[Směrovou atributy](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a6538-341">[Directional Attributes](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span></span>  
 [<span data-ttu-id="a6538-342">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="a6538-342">Copying and Pinning</span></span>](copying-and-pinning.md)
