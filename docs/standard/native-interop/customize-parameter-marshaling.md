---
title: Přizpůsobení zařazování parametrů – .NET
description: Naučte se, jak přizpůsobit, jak .NET zařazování parametrů do nativní reprezentace.
ms.date: 01/18/2019
ms.openlocfilehash: 1999cad057875f15b283421f87f485c2e5ca2306
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374309"
---
# <a name="customizing-parameter-marshaling"></a>Přizpůsobení zařazování parametrů

Pokud chování při zařazování výchozích parametrů modulu .NET runtime nezpůsobí, můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> atribut k přizpůsobení způsobu zařazení parametrů.

## <a name="customizing-string-parameters"></a>Přizpůsobení parametrů řetězce

Rozhraní .NET má různé formáty pro zařazování řetězců. Tyto metody jsou rozděleny do samostatných oddílů v řetězcích stylu C a ve formátech řetězců orientovaných na systém Windows.

### <a name="c-style-strings"></a>Řetězce ve stylu jazyka C

Každý z těchto formátů předá řetězec zakončený hodnotou null do nativního kódu. Liší se v kódování nativního řetězce.

| `System.Runtime.InteropServices.UnmanagedType`osa | Kódování |
|------------------------------------------------------|----------|
| Typem LPStr | ANSI |
| LPUTF8Str | UTF-8 |
| LPWStr | UTF-16 |
| LPTStr | UTF-16 |

<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType>Formát je mírně odlišný. Podobně jako `LPWStr` , zařazování řetězce do nativního řetězce ve stylu jazyka C kódovaného v kódování UTF-16. Spravovaný podpis však předáte do řetězce odkazem a na základě odpovídajícího nativního podpisu převezme řetězec podle hodnoty. Tento rozdíl umožňuje použít nativní rozhraní API, které přebírá řetězec podle hodnoty a upravuje ho místně bez nutnosti použít `StringBuilder` . Doporučujeme, abyste ručně používali tento formát, protože je náchylný k záměně s neshodou nativních a spravovaných podpisů.

### <a name="windows-centric-string-formats"></a>Formáty řetězců orientované na systém Windows

Při interakci s rozhraními COM nebo OLE pravděpodobně zjistíte, že nativní funkce přebírají řetězce jako `BSTR` argumenty. Nespravovaný typ můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> k zařazení řetězce jako `BSTR` .

Pokud spolupracujete s rozhraními API WinRT, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> formát k zařazení řetězce jako `HSTRING` .

## <a name="customizing-array-parameters"></a>Přizpůsobení parametrů pole

Rozhraní .NET také poskytuje více způsobů zařazování parametrů pole. Pokud voláte rozhraní API, které přijímá pole ve stylu jazyka C, použijte <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> nespravovaný typ. Pokud hodnoty v poli vyžadují přizpůsobené zařazování, můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> pole v `[MarshalAs]` atributu pro tuto položku.

Pokud používáte rozhraní API modelu COM, budete pravděpodobně muset zařadit parametry pole jako `SAFEARRAY*` s. K tomu můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> nespravovaný typ. Výchozí typ prvků `SAFEARRAY` lze v tabulce pro [přizpůsobení `object` polí](./customize-struct-marshaling.md#marshal-systemobject)zobrazit. Pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> polí a můžete <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> přizpůsobit přesný typ prvku `SAFEARRAY` .

## <a name="customizing-boolean-or-decimal-parameters"></a>Přizpůsobení logických nebo desetinných parametrů

Informace o zařazování logických nebo desetinných parametrů najdete v tématu [přizpůsobení zařazování struktury](customize-struct-marshaling.md).

## <a name="customizing-object-parameters-windows-only"></a>Přizpůsobení parametrů objektu (pouze systém Windows)

V systému Windows modul runtime .NET poskytuje řadu různých způsobů zařazování parametrů objektů do nativního kódu.

### <a name="marshaling-as-specific-com-interfaces"></a>Zařazování jako specifických rozhraní COM

Pokud rozhraní API převezme ukazatel na objekt modelu COM, můžete použít libovolný z následujících formátů pro `UnmanagedType` `object` parametr-Type a sdělit tak technologii .NET, aby byla zařazování jako tato konkrétní rozhraní:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Kromě toho, pokud je váš typ označený `[ComVisible(true)]` nebo zařadíte `object` typ, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> formát pro zařazování objektu jako vydanou obálku modelu COM pro zobrazení typu com.

### <a name="marshaling-to-a-variant"></a>Zařazování do`VARIANT`

Pokud vaše nativní rozhraní API přebírá Win32 `VARIANT` , můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> Formát v `object` parametru k zařazení objektů jako `VARIANT` s. Přečtěte si dokumentaci k [přizpůsobení `object` polí](customize-struct-marshaling.md#marshal-systemobject) pro mapování mezi typy a typy .NET `VARIANT` .

### <a name="custom-marshalers"></a>Vlastní zařazovací modul

Pokud chcete vytvořit projekt nativního rozhraní modelu COM do jiného spravovaného typu, můžete použít `UnmanagedType.CustomMarshaler` Formát a implementaci <xref:System.Runtime.InteropServices.ICustomMarshaler> k poskytnutí vlastního kódu zařazování.
