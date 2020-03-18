---
title: Přizpůsobení zařazování parametrů - .NET
description: Zjistěte, jak přizpůsobit, jak rozhraní .NET zařazuje parametry do nativní reprezentace.
ms.date: 01/18/2019
ms.openlocfilehash: ff646ad942cf051ce90cd75b24c8562e536182d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400363"
---
# <a name="customizing-parameter-marshaling"></a>Přizpůsobení zařazování parametrů

Pokud chování zařazování výchozího parametru .NET runtime nefunguje, <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> co chcete, můžete pomocí atributu přizpůsobit způsob zařazování parametrů.

## <a name="customizing-string-parameters"></a>Přizpůsobení parametrů řetězce

Rozhraní .NET má různé formáty pro zařazování řetězců. Tyto metody jsou rozděleny do různých oddílů na řetězce stylu C a formáty řetězců zaměřených na systém Windows.

### <a name="c-style-strings"></a>Řetězce stylu C

Každý z těchto formátů předá nativnímu kódu řetězec s ukončeným hodnotou null. Liší se kódováním nativního řetězce.

| `System.Runtime.InteropServices.UnmanagedType`Hodnotu | Kódování |
|------------------------------------------------------|----------|
| LPStr | ANSI |
| LPUTF8Str | UTF-8 |
| LPWStr | UTF-16 |
| Lptstr | UTF-16 |

Formát <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> je mírně odlišný. Stejně jako `LPWStr`, zařazuje řetězec na nativní řetězec ve stylu C kódovaný v UTF-16. Spravovaný podpis však má předáte v řetězci odkazem a odpovídající nativní podpis trvá řetězec podle hodnoty. Toto rozlišení umožňuje použít nativní rozhraní API, které přebírá řetězec podle hodnoty a `StringBuilder`upravuje jej na místě bez nutnosti použití rozhraní . Doporučujeme nepoužívat tento formát ručně, protože je náchylný k záměně s neodpovídajícími nativními a spravovanými podpisy.

### <a name="windows-centric-string-formats"></a>Formáty řetězců zaměřených na systém Windows

Při interakci s rozhraními COM nebo OLE pravděpodobně zjistíte, že `BSTR` nativní funkce berou řetězce jako argumenty. <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> Nespravovaný typ můžete použít k `BSTR`zařazování řetězce jako .

Pokud pracujete s winrt api, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> formát zařazovat řetězec jako `HSTRING`.

## <a name="customizing-array-parameters"></a>Přizpůsobení parametrů pole

Rozhraní .NET také poskytuje několik způsobů, jak zařadit parametry pole. Pokud voláte rozhraní API, které přebírá pole ve <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> stylu C, použijte nespravovaný typ. Pokud hodnoty v poli potřebují vlastní zařazování, můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> pole na `[MarshalAs]` atribut pro tento.

Pokud používáte rozhraní API COM, budete pravděpodobně muset zařadit `SAFEARRAY*`parametry pole jako s. Chcete-li tak učinit, <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> můžete použít nespravovaný typ. Výchozí typ prvků prvků `SAFEARRAY` lze zobrazit v tabulce na [přizpůsobení `object` polí](./customize-struct-marshaling.md#marshaling-systemobjects). Pole <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> můžete použít k přizpůsobení přesného `SAFEARRAY`typu prvku rozhraní .

## <a name="customizing-boolean-or-decimal-parameters"></a>Přizpůsobení logických nebo desetinných parametrů

Informace o zařazování logických nebo desítkových parametrů naleznete v [tématu Přizpůsobení zařazování struktury](customize-struct-marshaling.md).

## <a name="customizing-object-parameters-windows-only"></a>Přizpůsobení parametrů objektu (pouze systém Windows)

V systému Windows poskytuje běh .NET řadu různých způsobů, jak zařadit parametry objektu do nativního kódu.

### <a name="marshaling-as-specific-com-interfaces"></a>Zařazování jako specifická rozhraní COM

Pokud vaše rozhraní API přebírá ukazatel na objekt COM, `UnmanagedType` můžete použít `object`některý z následujících formátů parametru -typed a sdělit rozhraní .NET jako zařazovací jako tato konkrétní rozhraní:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Navíc pokud je váš `[ComVisible(true)]` typ označen nebo `object` zařazujete <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> typ, můžete použít formát zařazovat objekt jako com volatelné obálky pro zobrazení COM vašeho typu.

### <a name="marshaling-to-a-variant"></a>Zařazování do`VARIANT`

Pokud vaše nativní rozhraní `VARIANT`API trvá Win32 , můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> formát na `object` parametr zařadit objekty jako `VARIANT`s. V dokumentaci k [přizpůsobení `object` polí](customize-struct-marshaling.md#marshaling-systemobjects) pro mapování `VARIANT` mezi typy .NET a typy.

### <a name="custom-marshalers"></a>Vlastní zařazovače

Pokud chcete promítnout nativní rozhraní COM do jiného spravovaného `UnmanagedType.CustomMarshaler` <xref:System.Runtime.InteropServices.ICustomMarshaler> typu, můžete použít formát a implementaci poskytnout vlastní zařazovací kód.
