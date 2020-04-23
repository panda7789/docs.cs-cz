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
ms.openlocfilehash: e0de715a3ed33eedf212fc3e0e9930c9cbaa0a38
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123594"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="cbd18-102">Výchozí zařazování pro objekty</span><span class="sxs-lookup"><span data-stu-id="cbd18-102">Default Marshaling for Objects</span></span>

<span data-ttu-id="cbd18-103">Parametry a pole, které <xref:System.Object?displayProperty=nameWithType> jsou zadány jako mohou být zpřístupněny nespravovanému kódu jako jeden z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="cbd18-103">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>

- <span data-ttu-id="cbd18-104">Varianta, pokud je objekt parametrem.</span><span class="sxs-lookup"><span data-stu-id="cbd18-104">A variant when the object is a parameter.</span></span>

- <span data-ttu-id="cbd18-105">Rozhraní, když je objekt polem struktury.</span><span class="sxs-lookup"><span data-stu-id="cbd18-105">An interface when the object is a structure field.</span></span>

<span data-ttu-id="cbd18-106">Zařazování pro typy objektů podporuje pouze zprostředkovatel komunikace s objekty COM.</span><span class="sxs-lookup"><span data-stu-id="cbd18-106">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="cbd18-107">Výchozím chováním je zařazování objektů do variant modelu COM.</span><span class="sxs-lookup"><span data-stu-id="cbd18-107">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="cbd18-108">Tato pravidla se vztahují pouze na **objekt** typu a nevztahují se na objekty silného typu, které jsou odvozeny z třídy **Object** .</span><span class="sxs-lookup"><span data-stu-id="cbd18-108">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>

## <a name="marshaling-options"></a><span data-ttu-id="cbd18-109">Možnosti zařazování</span><span class="sxs-lookup"><span data-stu-id="cbd18-109">Marshaling Options</span></span>

<span data-ttu-id="cbd18-110">V následující tabulce jsou uvedeny možnosti zařazování pro datový typ **objektu** .</span><span class="sxs-lookup"><span data-stu-id="cbd18-110">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="cbd18-111"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atribut poskytuje několik <xref:System.Runtime.InteropServices.UnmanagedType> hodnot výčtu pro zařazování objektů.</span><span class="sxs-lookup"><span data-stu-id="cbd18-111">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>

|<span data-ttu-id="cbd18-112">Typ výčtu</span><span class="sxs-lookup"><span data-stu-id="cbd18-112">Enumeration type</span></span>|<span data-ttu-id="cbd18-113">Popis nespravovaného formátu</span><span class="sxs-lookup"><span data-stu-id="cbd18-113">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="cbd18-114">**UnmanagedType. struct**</span><span class="sxs-lookup"><span data-stu-id="cbd18-114">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="cbd18-115">(výchozí pro parametry)</span><span class="sxs-lookup"><span data-stu-id="cbd18-115">(default for parameters)</span></span>|<span data-ttu-id="cbd18-116">Variant ve stylu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="cbd18-116">A COM-style variant.</span></span>|
|<span data-ttu-id="cbd18-117">**UnmanagedType. Interface**</span><span class="sxs-lookup"><span data-stu-id="cbd18-117">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="cbd18-118">Rozhraní **IDispatch** , pokud je to možné; v opačném případě rozhraní **IUnknown** .</span><span class="sxs-lookup"><span data-stu-id="cbd18-118">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|
|<span data-ttu-id="cbd18-119">**UnmanagedType. IUnknown**</span><span class="sxs-lookup"><span data-stu-id="cbd18-119">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="cbd18-120">(výchozí pro pole)</span><span class="sxs-lookup"><span data-stu-id="cbd18-120">(default for fields)</span></span>|<span data-ttu-id="cbd18-121">Rozhraní **IUnknown** .</span><span class="sxs-lookup"><span data-stu-id="cbd18-121">An **IUnknown** interface.</span></span>|
|<span data-ttu-id="cbd18-122">**UnmanagedType. IDispatch**</span><span class="sxs-lookup"><span data-stu-id="cbd18-122">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="cbd18-123">Rozhraní **IDispatch** .</span><span class="sxs-lookup"><span data-stu-id="cbd18-123">An **IDispatch** interface.</span></span>|

<span data-ttu-id="cbd18-124">Následující příklad ukazuje definici spravovaného rozhraní pro `MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="cbd18-124">The following example shows the managed interface definition for `MarshalObject`.</span></span>

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

<span data-ttu-id="cbd18-125">Následující kód exportuje `MarshalObject` rozhraní do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="cbd18-125">The following code exports the `MarshalObject` interface to a type library.</span></span>

```cpp
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
> <span data-ttu-id="cbd18-126">Zařazovací modul Interop automaticky uvolňuje všechny přidělené objekty v rámci varianty po volání.</span><span class="sxs-lookup"><span data-stu-id="cbd18-126">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>

<span data-ttu-id="cbd18-127">Následující příklad ukazuje formátovaný typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cbd18-127">The following example shows a formatted value type.</span></span>

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

<span data-ttu-id="cbd18-128">Následující kód exportuje formátovaný typ do knihovny typů.</span><span class="sxs-lookup"><span data-stu-id="cbd18-128">The following code exports the formatted type to a type library.</span></span>

```cpp
struct ObjectHolder {
   VARIANT o1;
   IDispatch *o2;
}
```

## <a name="marshaling-object-to-interface"></a><span data-ttu-id="cbd18-129">Zařazování objektu na rozhraní</span><span class="sxs-lookup"><span data-stu-id="cbd18-129">Marshaling Object to Interface</span></span>

<span data-ttu-id="cbd18-130">Když je objekt v modelu COM vystaven jako rozhraní, toto rozhraní je rozhraní třídy pro spravovaný typ <xref:System.Object> (rozhraní **_object** ).</span><span class="sxs-lookup"><span data-stu-id="cbd18-130">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="cbd18-131">Toto rozhraní je typu **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) nebo **IUnknown** (**UnmanagedType. IUnknown**) ve výsledné knihovně typů.</span><span class="sxs-lookup"><span data-stu-id="cbd18-131">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="cbd18-132">Klienti modelu COM mohou dynamicky volat členy spravované třídy nebo všech členů implementovaných svými odvozenými třídami prostřednictvím rozhraní **_object** .</span><span class="sxs-lookup"><span data-stu-id="cbd18-132">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="cbd18-133">Klient může také volat metodu **QueryInterface** , aby získala jakékoli jiné rozhraní explicitně implementované spravovaným typem.</span><span class="sxs-lookup"><span data-stu-id="cbd18-133">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>

## <a name="marshaling-object-to-variant"></a><span data-ttu-id="cbd18-134">Zařazování objektu na typ variant</span><span class="sxs-lookup"><span data-stu-id="cbd18-134">Marshaling Object to Variant</span></span>

<span data-ttu-id="cbd18-135">Při zařazování objektu na variantu je interní typ variant určen za běhu na základě následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="cbd18-135">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>

- <span data-ttu-id="cbd18-136">Pokud odkaz na objekt má hodnotu null (**Nothing** v Visual Basic), objekt je zařazen do varianty typu **VT_EMPTY**.</span><span class="sxs-lookup"><span data-stu-id="cbd18-136">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>

- <span data-ttu-id="cbd18-137">Je-li objekt instancí libovolného typu, který je uveden v následující tabulce, je výsledný typ variant určen pravidly integrovanými do zařazovacího modulu a zobrazeným v tabulce.</span><span class="sxs-lookup"><span data-stu-id="cbd18-137">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>

- <span data-ttu-id="cbd18-138">Další objekty, které potřebují explicitně řídit chování zařazování, mohou implementovat <xref:System.IConvertible> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cbd18-138">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="cbd18-139">V takovém případě typ variant je určen kódem typu vráceným z <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="cbd18-139">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cbd18-140">V opačném případě je objekt zařazen jako typ variant typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="cbd18-140">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>

### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="cbd18-141">Zařazování typů systému do varianty</span><span class="sxs-lookup"><span data-stu-id="cbd18-141">Marshaling System Types to Variant</span></span>

<span data-ttu-id="cbd18-142">V následující tabulce jsou uvedeny typy spravovaných objektů a jejich odpovídající typy variant modelu COM.</span><span class="sxs-lookup"><span data-stu-id="cbd18-142">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="cbd18-143">Tyto typy jsou převedeny pouze v případě, že signatura volané metody je typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cbd18-143">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>

|<span data-ttu-id="cbd18-144">typ objektu</span><span class="sxs-lookup"><span data-stu-id="cbd18-144">Object type</span></span>|<span data-ttu-id="cbd18-145">Typ variant modelu COM</span><span class="sxs-lookup"><span data-stu-id="cbd18-145">COM variant type</span></span>|
|-----------------|----------------------|
|<span data-ttu-id="cbd18-146">Nulový odkaz na objekt (**Nothing** v Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbd18-146">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="cbd18-147">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="cbd18-147">**VT_EMPTY**</span></span>|
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="cbd18-148">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="cbd18-148">**VT_NULL**</span></span>|
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="cbd18-149">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="cbd18-149">**VT_ERROR**</span></span>|
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="cbd18-150">**VT_ERROR** s **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="cbd18-150">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="cbd18-151">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="cbd18-151">**VT_DISPATCH**</span></span>|
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="cbd18-152">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="cbd18-152">**VT_UNKNOWN**</span></span>|
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="cbd18-153">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="cbd18-153">**VT_CY**</span></span>|
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="cbd18-154">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="cbd18-154">**VT_BOOL**</span></span>|
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="cbd18-155">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="cbd18-155">**VT_I1**</span></span>|
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="cbd18-156">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="cbd18-156">**VT_UI1**</span></span>|
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="cbd18-157">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="cbd18-157">**VT_I2**</span></span>|
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="cbd18-158">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="cbd18-158">**VT_UI2**</span></span>|
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="cbd18-159">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="cbd18-159">**VT_I4**</span></span>|
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="cbd18-160">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="cbd18-160">**VT_UI4**</span></span>|
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="cbd18-161">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="cbd18-161">**VT_I8**</span></span>|
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="cbd18-162">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="cbd18-162">**VT_UI8**</span></span>|
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="cbd18-163">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="cbd18-163">**VT_R4**</span></span>|
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="cbd18-164">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="cbd18-164">**VT_R8**</span></span>|
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="cbd18-165">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="cbd18-165">**VT_DECIMAL**</span></span>|
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="cbd18-166">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="cbd18-166">**VT_DATE**</span></span>|
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="cbd18-167">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="cbd18-167">**VT_BSTR**</span></span>|
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="cbd18-168">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="cbd18-168">**VT_INT**</span></span>|
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="cbd18-169">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="cbd18-169">**VT_UINT**</span></span>|
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="cbd18-170">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="cbd18-170">**VT_ARRAY**</span></span>|

<span data-ttu-id="cbd18-171">V následujícím `MarshalObject` příkladu kódu ukazuje, jak předat různé typy variant do serveru com, pomocí rozhraní definovaného v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cbd18-171">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>

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

<span data-ttu-id="cbd18-172">Typy modelu <xref:System.Runtime.InteropServices.ErrorWrapper>com, které nemají odpovídající spravované typy, lze zařadit pomocí tříd obálky, jako jsou <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, a <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span><span class="sxs-lookup"><span data-stu-id="cbd18-172">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="cbd18-173">Následující příklad kódu ukazuje, jak tyto obálky použít k předávání různých typů variant serveru COM.</span><span class="sxs-lookup"><span data-stu-id="cbd18-173">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>

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

<span data-ttu-id="cbd18-174">Obálkové třídy jsou definovány v <xref:System.Runtime.InteropServices> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cbd18-174">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>

### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="cbd18-175">Zařazování rozhraní IConvertible k variantě</span><span class="sxs-lookup"><span data-stu-id="cbd18-175">Marshaling the IConvertible Interface to Variant</span></span>

<span data-ttu-id="cbd18-176">Jiné typy než ty, které jsou uvedeny v předchozí části, mohou řídit, jak jsou zařazeny <xref:System.IConvertible> implementací rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cbd18-176">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="cbd18-177">Pokud objekt implementuje rozhraní **IConvertible** , typ variant modelu COM je určen za běhu podle hodnoty <xref:System.TypeCode> výčtu vráceného z <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="cbd18-177">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="cbd18-178">V následující tabulce jsou uvedeny možné hodnoty pro výčet **TypeCode** a odpovídající typ variant modelu COM pro každou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cbd18-178">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>

|<span data-ttu-id="cbd18-179">Kódu</span><span class="sxs-lookup"><span data-stu-id="cbd18-179">TypeCode</span></span>|<span data-ttu-id="cbd18-180">Typ variant modelu COM</span><span class="sxs-lookup"><span data-stu-id="cbd18-180">COM variant type</span></span>|
|--------------|----------------------|
|<span data-ttu-id="cbd18-181">**TypeCode. Empty**</span><span class="sxs-lookup"><span data-stu-id="cbd18-181">**TypeCode.Empty**</span></span>|<span data-ttu-id="cbd18-182">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="cbd18-182">**VT_EMPTY**</span></span>|
|<span data-ttu-id="cbd18-183">**TypeCode. Object**</span><span class="sxs-lookup"><span data-stu-id="cbd18-183">**TypeCode.Object**</span></span>|<span data-ttu-id="cbd18-184">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="cbd18-184">**VT_UNKNOWN**</span></span>|
|<span data-ttu-id="cbd18-185">**TypeCode. DBNull**</span><span class="sxs-lookup"><span data-stu-id="cbd18-185">**TypeCode.DBNull**</span></span>|<span data-ttu-id="cbd18-186">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="cbd18-186">**VT_NULL**</span></span>|
|<span data-ttu-id="cbd18-187">**TypeCode. Boolean**</span><span class="sxs-lookup"><span data-stu-id="cbd18-187">**TypeCode.Boolean**</span></span>|<span data-ttu-id="cbd18-188">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="cbd18-188">**VT_BOOL**</span></span>|
|<span data-ttu-id="cbd18-189">**TypeCode. Char**</span><span class="sxs-lookup"><span data-stu-id="cbd18-189">**TypeCode.Char**</span></span>|<span data-ttu-id="cbd18-190">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="cbd18-190">**VT_UI2**</span></span>|
|<span data-ttu-id="cbd18-191">**TypeCode. SByte**</span><span class="sxs-lookup"><span data-stu-id="cbd18-191">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="cbd18-192">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="cbd18-192">**VT_I1**</span></span>|
|<span data-ttu-id="cbd18-193">**TypeCode. Byte**</span><span class="sxs-lookup"><span data-stu-id="cbd18-193">**TypeCode.Byte**</span></span>|<span data-ttu-id="cbd18-194">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="cbd18-194">**VT_UI1**</span></span>|
|<span data-ttu-id="cbd18-195">**TypeCode. Int16**</span><span class="sxs-lookup"><span data-stu-id="cbd18-195">**TypeCode.Int16**</span></span>|<span data-ttu-id="cbd18-196">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="cbd18-196">**VT_I2**</span></span>|
|<span data-ttu-id="cbd18-197">**TypeCode. UInt16**</span><span class="sxs-lookup"><span data-stu-id="cbd18-197">**TypeCode.UInt16**</span></span>|<span data-ttu-id="cbd18-198">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="cbd18-198">**VT_UI2**</span></span>|
|<span data-ttu-id="cbd18-199">**TypeCode. Int32**</span><span class="sxs-lookup"><span data-stu-id="cbd18-199">**TypeCode.Int32**</span></span>|<span data-ttu-id="cbd18-200">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="cbd18-200">**VT_I4**</span></span>|
|<span data-ttu-id="cbd18-201">**TypeCode. UInt32**</span><span class="sxs-lookup"><span data-stu-id="cbd18-201">**TypeCode.UInt32**</span></span>|<span data-ttu-id="cbd18-202">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="cbd18-202">**VT_UI4**</span></span>|
|<span data-ttu-id="cbd18-203">**TypeCode. Int64**</span><span class="sxs-lookup"><span data-stu-id="cbd18-203">**TypeCode.Int64**</span></span>|<span data-ttu-id="cbd18-204">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="cbd18-204">**VT_I8**</span></span>|
|<span data-ttu-id="cbd18-205">**TypeCode. UInt64**</span><span class="sxs-lookup"><span data-stu-id="cbd18-205">**TypeCode.UInt64**</span></span>|<span data-ttu-id="cbd18-206">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="cbd18-206">**VT_UI8**</span></span>|
|<span data-ttu-id="cbd18-207">**TypeCode. Single**</span><span class="sxs-lookup"><span data-stu-id="cbd18-207">**TypeCode.Single**</span></span>|<span data-ttu-id="cbd18-208">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="cbd18-208">**VT_R4**</span></span>|
|<span data-ttu-id="cbd18-209">**TypeCode. Double**</span><span class="sxs-lookup"><span data-stu-id="cbd18-209">**TypeCode.Double**</span></span>|<span data-ttu-id="cbd18-210">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="cbd18-210">**VT_R8**</span></span>|
|<span data-ttu-id="cbd18-211">**TypeCode. Decimal**</span><span class="sxs-lookup"><span data-stu-id="cbd18-211">**TypeCode.Decimal**</span></span>|<span data-ttu-id="cbd18-212">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="cbd18-212">**VT_DECIMAL**</span></span>|
|<span data-ttu-id="cbd18-213">**TypeCode. DateTime**</span><span class="sxs-lookup"><span data-stu-id="cbd18-213">**TypeCode.DateTime**</span></span>|<span data-ttu-id="cbd18-214">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="cbd18-214">**VT_DATE**</span></span>|
|<span data-ttu-id="cbd18-215">**TypeCode. String**</span><span class="sxs-lookup"><span data-stu-id="cbd18-215">**TypeCode.String**</span></span>|<span data-ttu-id="cbd18-216">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="cbd18-216">**VT_BSTR**</span></span>|
|<span data-ttu-id="cbd18-217">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cbd18-217">Not supported.</span></span>|<span data-ttu-id="cbd18-218">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="cbd18-218">**VT_INT**</span></span>|
|<span data-ttu-id="cbd18-219">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cbd18-219">Not supported.</span></span>|<span data-ttu-id="cbd18-220">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="cbd18-220">**VT_UINT**</span></span>|
|<span data-ttu-id="cbd18-221">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cbd18-221">Not supported.</span></span>|<span data-ttu-id="cbd18-222">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="cbd18-222">**VT_ARRAY**</span></span>|
|<span data-ttu-id="cbd18-223">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cbd18-223">Not supported.</span></span>|<span data-ttu-id="cbd18-224">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="cbd18-224">**VT_RECORD**</span></span>|
|<span data-ttu-id="cbd18-225">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cbd18-225">Not supported.</span></span>|<span data-ttu-id="cbd18-226">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="cbd18-226">**VT_CY**</span></span>|
|<span data-ttu-id="cbd18-227">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cbd18-227">Not supported.</span></span>|<span data-ttu-id="cbd18-228">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="cbd18-228">**VT_VARIANT**</span></span>|

<span data-ttu-id="cbd18-229">Hodnota variant modelu COM je určena voláním rozhraní *typu* **IConvertible.to** , kde **pro** *typ* je rutina převodu, která odpovídá typu, který byl vrácen z **IConvertible. GetTypeCode**.</span><span class="sxs-lookup"><span data-stu-id="cbd18-229">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="cbd18-230">Například objekt, který vrací **TypeCode. Double** z **IConvertible. GetTypeCode** je zařazen jako typ variant modelu COM typu **VT_R8**.</span><span class="sxs-lookup"><span data-stu-id="cbd18-230">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="cbd18-231">Můžete získat hodnotu Variant (uloženou v poli **dblVal** variant modelu COM) přetypováním do rozhraní **IConvertible** a voláním <xref:System.IConvertible.ToDouble%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cbd18-231">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>

## <a name="marshaling-variant-to-object"></a><span data-ttu-id="cbd18-232">Zařazování variant do objektu</span><span class="sxs-lookup"><span data-stu-id="cbd18-232">Marshaling Variant to Object</span></span>

<span data-ttu-id="cbd18-233">Při zařazování variant do objektu, typ a někdy hodnota pro zařazování variant určuje typ vytvořeného objektu.</span><span class="sxs-lookup"><span data-stu-id="cbd18-233">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="cbd18-234">Následující tabulka určuje každý typ variant a odpovídající typ objektu, který zařazovací modul vytvoří, když je hodnota typu variant předána z modelu COM do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cbd18-234">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>

|<span data-ttu-id="cbd18-235">Typ variant modelu COM</span><span class="sxs-lookup"><span data-stu-id="cbd18-235">COM variant type</span></span>|<span data-ttu-id="cbd18-236">typ objektu</span><span class="sxs-lookup"><span data-stu-id="cbd18-236">Object type</span></span>|
|----------------------|-----------------|
|<span data-ttu-id="cbd18-237">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="cbd18-237">**VT_EMPTY**</span></span>|<span data-ttu-id="cbd18-238">Nulový odkaz na objekt (**Nothing** v Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbd18-238">Null object reference (**Nothing** in Visual Basic).</span></span>|
|<span data-ttu-id="cbd18-239">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="cbd18-239">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-240">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="cbd18-240">**VT_DISPATCH**</span></span>|<span data-ttu-id="cbd18-241">**System. __ComObject** nebo null if (pdispVal = = null)</span><span class="sxs-lookup"><span data-stu-id="cbd18-241">**System.__ComObject** or null if (pdispVal == null)</span></span>|
|<span data-ttu-id="cbd18-242">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="cbd18-242">**VT_UNKNOWN**</span></span>|<span data-ttu-id="cbd18-243">**System. __ComObject** nebo null if (punkVal = = null)</span><span class="sxs-lookup"><span data-stu-id="cbd18-243">**System.__ComObject** or null if (punkVal == null)</span></span>|
|<span data-ttu-id="cbd18-244">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="cbd18-244">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-245">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="cbd18-245">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-246">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="cbd18-246">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-247">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="cbd18-247">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-248">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="cbd18-248">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-249">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="cbd18-249">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-250">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="cbd18-250">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-251">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="cbd18-251">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-252">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="cbd18-252">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-253">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="cbd18-253">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-254">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="cbd18-254">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-255">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="cbd18-255">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-256">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="cbd18-256">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-257">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="cbd18-257">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-258">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="cbd18-258">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-259">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="cbd18-259">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-260">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="cbd18-260">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-261">**VT_ARRAY** &#124; **VT_**\*</span><span class="sxs-lookup"><span data-stu-id="cbd18-261">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-262">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="cbd18-262">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="cbd18-263">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="cbd18-263">**VT_RECORD**</span></span>|<span data-ttu-id="cbd18-264">Odpovídající zabalený typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cbd18-264">Corresponding boxed value type.</span></span>|
|<span data-ttu-id="cbd18-265">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="cbd18-265">**VT_VARIANT**</span></span>|<span data-ttu-id="cbd18-266">Není podporováno.</span><span class="sxs-lookup"><span data-stu-id="cbd18-266">Not supported.</span></span>|

<span data-ttu-id="cbd18-267">Typy variant předané z modelu COM do spravovaného kódu a poté zpět do modelu COM nemusí zachovat stejný typ variant pro dobu trvání volání.</span><span class="sxs-lookup"><span data-stu-id="cbd18-267">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="cbd18-268">Zvažte, co se stane, když je typ variant typu **VT_DISPATCH** předán z modelu COM do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cbd18-268">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="cbd18-269">V průběhu zařazování je varianta převedena na <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cbd18-269">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cbd18-270">Pokud je **objekt** předán zpět do modelu COM, je zařazen zpět na variantu typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="cbd18-270">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="cbd18-271">Není nijak zaručeno, že varianta vytvořená při zařazování objektu ze spravovaného kódu do modelu COM bude stejného typu jako původně použitá varianta k vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="cbd18-271">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>

## <a name="marshaling-byref-variants"></a><span data-ttu-id="cbd18-272">Zařazování variant typu ByRef</span><span class="sxs-lookup"><span data-stu-id="cbd18-272">Marshaling ByRef Variants</span></span>

<span data-ttu-id="cbd18-273">I když samotné varianty mohou být předány hodnotou nebo odkazem, příznak **VT_BYREF** lze také použít s libovolným typem variant k označení toho, že obsah varianty je předáván odkazem namísto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cbd18-273">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="cbd18-274">Rozdíl mezi zařazováním variant podle odkazu a zařazováním typu variant se sadou příznaků **VT_BYREF** může být matoucí.</span><span class="sxs-lookup"><span data-stu-id="cbd18-274">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="cbd18-275">Rozdíly jsou znázorněny na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="cbd18-275">The following illustration clarifies the differences:</span></span>

<span data-ttu-id="cbd18-276">![Diagram, který zobrazuje variantu předanou v zásobníku.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span><span class="sxs-lookup"><span data-stu-id="cbd18-276">![Diagram that shows variant passed on the stack.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span></span>
<span data-ttu-id="cbd18-277">Varianty předané hodnotou a odkazem</span><span class="sxs-lookup"><span data-stu-id="cbd18-277">Variants passed by value and by reference</span></span>

<span data-ttu-id="cbd18-278">**Výchozí chování zařazování objektů a variant podle hodnoty**</span><span class="sxs-lookup"><span data-stu-id="cbd18-278">**Default behavior for marshaling objects and variants by value**</span></span>

- <span data-ttu-id="cbd18-279">Při předávání objektů ze spravovaného kódu do modelu COM je obsah objektu zkopírován do nového objektu variant vytvořeného zařazováním pomocí pravidel definovaných v [zařazování objektu na typ variant](#marshaling-object-to-variant).</span><span class="sxs-lookup"><span data-stu-id="cbd18-279">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#marshaling-object-to-variant).</span></span> <span data-ttu-id="cbd18-280">Změny provedené v variantě na nespravované straně nejsou šířeny zpět do původního objektu při návratu ze volání.</span><span class="sxs-lookup"><span data-stu-id="cbd18-280">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>

- <span data-ttu-id="cbd18-281">Při předávání variant z modelu COM do spravovaného kódu je obsah varianty zkopírován do nově vytvořeného objektu pomocí pravidel definovaných v [zařazování variant do objektu](#marshaling-variant-to-object).</span><span class="sxs-lookup"><span data-stu-id="cbd18-281">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#marshaling-variant-to-object).</span></span> <span data-ttu-id="cbd18-282">Změny provedené u objektu na spravované straně nejsou šířeny zpět do původní varianty při návratu ze volání.</span><span class="sxs-lookup"><span data-stu-id="cbd18-282">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>

<span data-ttu-id="cbd18-283">**Výchozí chování zařazování objektů a variant podle odkazu**</span><span class="sxs-lookup"><span data-stu-id="cbd18-283">**Default behavior for marshaling objects and variants by reference**</span></span>

<span data-ttu-id="cbd18-284">Chcete-li rozšířit změny zpět volajícímu, musí být parametry předány odkazem.</span><span class="sxs-lookup"><span data-stu-id="cbd18-284">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="cbd18-285">Například můžete použít klíčové slovo **ref** v jazyce C# (nebo **ByRef** v Visual Basic spravovaný kód) k předání parametrů odkazem.</span><span class="sxs-lookup"><span data-stu-id="cbd18-285">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="cbd18-286">V modelu COM jsou parametry odkazu předány pomocí ukazatele, jako je \*\*například \*varianta \*\*.</span><span class="sxs-lookup"><span data-stu-id="cbd18-286">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>

- <span data-ttu-id="cbd18-287">Při předání objektu modelu COM odkazem vytvoří zařazovací objekt novou variantu a před provedením volání zkopíruje obsah odkazu na objekt do objektu variant.</span><span class="sxs-lookup"><span data-stu-id="cbd18-287">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="cbd18-288">Hodnota variant je předána nespravované funkci, kde uživatel je bezplatný pro změnu obsahu varianty.</span><span class="sxs-lookup"><span data-stu-id="cbd18-288">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="cbd18-289">Při návratu ze volání se všechny změny provedené v variantě nespravované strany rozšíří zpátky na původní objekt.</span><span class="sxs-lookup"><span data-stu-id="cbd18-289">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="cbd18-290">Pokud se typ variant liší od typu variant předaného volání, pak jsou změny šířeny zpět do objektu jiného typu.</span><span class="sxs-lookup"><span data-stu-id="cbd18-290">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="cbd18-291">To znamená, že typ objektu předaný do volání se může lišit od typu objektu vráceného voláním.</span><span class="sxs-lookup"><span data-stu-id="cbd18-291">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>

- <span data-ttu-id="cbd18-292">Při předávání typu variant ke spravovanému kódu odkazem vytvoří zařazovací modul nový objekt a před provedením volání zkopíruje obsah objektu variant do objektu.</span><span class="sxs-lookup"><span data-stu-id="cbd18-292">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="cbd18-293">Odkaz na objekt je předán do spravované funkce, kde je uživatel volné pro změnu objektu.</span><span class="sxs-lookup"><span data-stu-id="cbd18-293">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="cbd18-294">Při návratu ze volání jsou všechny změny provedené v odkazovaném objektu postoupeny zpět do původní varianty.</span><span class="sxs-lookup"><span data-stu-id="cbd18-294">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="cbd18-295">Pokud se typ objektu liší od typu objektu předaného volání, je změněn typ původní varianty a hodnota je rozšířena zpět do varianty.</span><span class="sxs-lookup"><span data-stu-id="cbd18-295">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="cbd18-296">Typ variant předaný do volání se pak může lišit od typu variant vráceného voláním.</span><span class="sxs-lookup"><span data-stu-id="cbd18-296">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>

 <span data-ttu-id="cbd18-297">**Výchozí chování pro zařazování typu variant se sadou příznakem VT_BYREF**</span><span class="sxs-lookup"><span data-stu-id="cbd18-297">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>

- <span data-ttu-id="cbd18-298">Typ variant předávaný do spravovaného kódu podle hodnoty může mít nastaven příznak **VT_BYREF** , který označuje, že varianta obsahuje odkaz namísto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cbd18-298">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="cbd18-299">V tomto případě je varianta stále zařazena do objektu, protože varianta je předávána hodnotou.</span><span class="sxs-lookup"><span data-stu-id="cbd18-299">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="cbd18-300">Zařazovací modul automaticky vyhodnotí obsah varianty a před provedením volání zkopíruje je do nově vytvořeného objektu.</span><span class="sxs-lookup"><span data-stu-id="cbd18-300">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="cbd18-301">Objekt je následně předán do spravované funkce; Při návratu ze volání se však objekt nerozšíří zpátky do původní varianty.</span><span class="sxs-lookup"><span data-stu-id="cbd18-301">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="cbd18-302">Změny provedené ve spravovaném objektu jsou ztraceny.</span><span class="sxs-lookup"><span data-stu-id="cbd18-302">Changes made to the managed object are lost.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="cbd18-303">Neexistuje žádný způsob, jak změnit hodnotu variant předanou hodnotou, a to i v případě, že má varianta nastaven příznak **VT_BYREF** .</span><span class="sxs-lookup"><span data-stu-id="cbd18-303">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>

- <span data-ttu-id="cbd18-304">Typ variant předávaný do spravovaného kódu odkazem může mít také nastaven příznak **VT_BYREF** , aby označoval, že varianta obsahuje jiný odkaz.</span><span class="sxs-lookup"><span data-stu-id="cbd18-304">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="cbd18-305">V takovém případě je varianta zařazena do objektu **ref** , protože varianta je předávána odkazem.</span><span class="sxs-lookup"><span data-stu-id="cbd18-305">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="cbd18-306">Zařazovací modul automaticky vyhodnotí obsah varianty a před provedením volání zkopíruje je do nově vytvořeného objektu.</span><span class="sxs-lookup"><span data-stu-id="cbd18-306">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="cbd18-307">Při návratu ze volání je hodnota objektu postoupena zpět na odkaz v rámci původní varianty pouze v případě, že objekt je stejného typu jako předaný objekt.</span><span class="sxs-lookup"><span data-stu-id="cbd18-307">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="cbd18-308">To znamená, že rozšíření nemění typ variant s nastaveným příznakem **VT_BYREF** .</span><span class="sxs-lookup"><span data-stu-id="cbd18-308">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="cbd18-309">Pokud se typ objektu změní během volání, <xref:System.InvalidCastException> dojde při návratu z volání.</span><span class="sxs-lookup"><span data-stu-id="cbd18-309">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>

<span data-ttu-id="cbd18-310">Následující tabulka shrnuje pravidla šíření pro varianty a objekty.</span><span class="sxs-lookup"><span data-stu-id="cbd18-310">The following table summarizes the propagation rules for variants and objects.</span></span>

|<span data-ttu-id="cbd18-311">From</span><span class="sxs-lookup"><span data-stu-id="cbd18-311">From</span></span>|<span data-ttu-id="cbd18-312">Akce</span><span class="sxs-lookup"><span data-stu-id="cbd18-312">To</span></span>|<span data-ttu-id="cbd18-313">Změny šířené zpět</span><span class="sxs-lookup"><span data-stu-id="cbd18-313">Changes propagated back</span></span>|
|----------|--------|-----------------------------|
|<span data-ttu-id="cbd18-314">**Varianta**  *v*</span><span class="sxs-lookup"><span data-stu-id="cbd18-314">**Variant**  *v*</span></span>|<span data-ttu-id="cbd18-315">**Objekt**  *o*</span><span class="sxs-lookup"><span data-stu-id="cbd18-315">**Object**  *o*</span></span>|<span data-ttu-id="cbd18-316">Never (Nikdy)</span><span class="sxs-lookup"><span data-stu-id="cbd18-316">Never</span></span>|
|<span data-ttu-id="cbd18-317">**Objekt**  *o*</span><span class="sxs-lookup"><span data-stu-id="cbd18-317">**Object**  *o*</span></span>|<span data-ttu-id="cbd18-318">**Varianta**  *v*</span><span class="sxs-lookup"><span data-stu-id="cbd18-318">**Variant**  *v*</span></span>|<span data-ttu-id="cbd18-319">Never (Nikdy)</span><span class="sxs-lookup"><span data-stu-id="cbd18-319">Never</span></span>|
|<span data-ttu-id="cbd18-320">**Variantní**   ***\****  *PV*</span><span class="sxs-lookup"><span data-stu-id="cbd18-320">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="cbd18-321">**Ref – objekt**  *o*</span><span class="sxs-lookup"><span data-stu-id="cbd18-321">**Ref Object**  *o*</span></span>|<span data-ttu-id="cbd18-322">Vždy</span><span class="sxs-lookup"><span data-stu-id="cbd18-322">Always</span></span>|
|<span data-ttu-id="cbd18-323">**Ref – objekt**  *o*</span><span class="sxs-lookup"><span data-stu-id="cbd18-323">**Ref object**  *o*</span></span>|<span data-ttu-id="cbd18-324">**Variantní**   ***\****  *PV*</span><span class="sxs-lookup"><span data-stu-id="cbd18-324">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="cbd18-325">Vždy</span><span class="sxs-lookup"><span data-stu-id="cbd18-325">Always</span></span>|
|<span data-ttu-id="cbd18-326">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span><span class="sxs-lookup"><span data-stu-id="cbd18-326">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="cbd18-327">**Objekt**  *o*</span><span class="sxs-lookup"><span data-stu-id="cbd18-327">**Object**  *o*</span></span>|<span data-ttu-id="cbd18-328">Never (Nikdy)</span><span class="sxs-lookup"><span data-stu-id="cbd18-328">Never</span></span>|
|<span data-ttu-id="cbd18-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span><span class="sxs-lookup"><span data-stu-id="cbd18-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="cbd18-330">**Ref – objekt**  *o*</span><span class="sxs-lookup"><span data-stu-id="cbd18-330">**Ref Object**  *o*</span></span>|<span data-ttu-id="cbd18-331">Pouze v případě, že se typ nezměnil.</span><span class="sxs-lookup"><span data-stu-id="cbd18-331">Only if the type has not changed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="cbd18-332">Viz také</span><span class="sxs-lookup"><span data-stu-id="cbd18-332">See also</span></span>

- [<span data-ttu-id="cbd18-333">Výchozí chování zařazování</span><span class="sxs-lookup"><span data-stu-id="cbd18-333">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="cbd18-334">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="cbd18-334">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="cbd18-335">[Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cbd18-335">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="cbd18-336">Kopírování a přichycování</span><span class="sxs-lookup"><span data-stu-id="cbd18-336">Copying and Pinning</span></span>](copying-and-pinning.md)
