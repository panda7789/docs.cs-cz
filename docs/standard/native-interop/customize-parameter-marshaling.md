---
title: Přizpůsobení zařazování parametrů – .NET
description: Naučte se, jak přizpůsobit, jak .NET zařazování parametrů do nativní reprezentace.
ms.date: 01/18/2019
ms.openlocfilehash: ff646ad942cf051ce90cd75b24c8562e536182d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400363"
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

<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> Formát je mírně odlišný. Podobně `LPWStr`jako, zařazování řetězce do nativního řetězce ve stylu jazyka C kódovaného v kódování UTF-16. Spravovaný podpis však předáte do řetězce odkazem a na základě odpovídajícího nativního podpisu převezme řetězec podle hodnoty. Tento rozdíl umožňuje použít nativní rozhraní API, které přebírá řetězec podle hodnoty a upravuje ho místně bez nutnosti použít `StringBuilder`. Doporučujeme, abyste ručně používali tento formát, protože je náchylný k záměně s neshodou nativních a spravovaných podpisů.

### <a name="windows-centric-string-formats"></a>Formáty řetězců orientované na systém Windows

Při interakci s rozhraními COM nebo OLE pravděpodobně zjistíte, že nativní funkce přebírají řetězce jako `BSTR` argumenty. <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> Nespravovaný typ můžete použít k zařazení řetězce jako `BSTR`.

Pokud spolupracujete s rozhraními API WinRT, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> formát k zařazení řetězce jako. `HSTRING`

## <a name="customizing-array-parameters"></a>Přizpůsobení parametrů pole

Rozhraní .NET také poskytuje více způsobů zařazování parametrů pole. Pokud voláte rozhraní API, které přijímá pole ve stylu jazyka C, použijte <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> nespravovaný typ. Pokud hodnoty v poli vyžadují přizpůsobené zařazování, můžete použít <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> pole v `[MarshalAs]` atributu pro tuto položku.

Pokud používáte rozhraní API modelu COM, budete pravděpodobně muset zařadit parametry pole jako `SAFEARRAY*`s. K tomu můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> nespravovaný typ. Výchozí typ prvků `SAFEARRAY` lze v tabulce pro [přizpůsobení `object` polí](./customize-struct-marshaling.md#marshaling-systemobjects)zobrazit. Pomocí polí <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> můžete přizpůsobit přesný typ prvku. `SAFEARRAY`

## <a name="customizing-boolean-or-decimal-parameters"></a>Přizpůsobení logických nebo desetinných parametrů

Informace o zařazování logických nebo desetinných parametrů najdete v tématu [přizpůsobení zařazování struktury](customize-struct-marshaling.md).

## <a name="customizing-object-parameters-windows-only"></a>Přizpůsobení parametrů objektu (pouze systém Windows)

V systému Windows modul runtime .NET poskytuje řadu různých způsobů zařazování parametrů objektů do nativního kódu.

### <a name="marshaling-as-specific-com-interfaces"></a>Zařazování jako specifických rozhraní COM

Pokud rozhraní API převezme ukazatel na objekt modelu COM, můžete použít libovolný z následujících `UnmanagedType` formátů pro parametr-Type `object`a sdělit tak technologii .NET, aby byla zařazování jako tato konkrétní rozhraní:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Kromě toho, pokud je váš typ `[ComVisible(true)]` označený nebo zařadíte `object` typ, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> formát pro zařazování objektu jako vydanou obálku modelu COM pro zobrazení typu com.

### <a name="marshaling-to-a-variant"></a>Zařazování do`VARIANT`

Pokud vaše nativní rozhraní API přebírá `VARIANT`Win32, můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> formát v `object` parametru k zařazení objektů jako `VARIANT`s. Přečtěte si dokumentaci [k `object` přizpůsobení polí](customize-struct-marshaling.md#marshaling-systemobjects) pro mapování mezi typy a `VARIANT` typy .NET.

### <a name="custom-marshalers"></a>Vlastní zařazovací modul

Pokud chcete vytvořit projekt nativního rozhraní modelu COM do jiného spravovaného typu, můžete použít `UnmanagedType.CustomMarshaler` formát a implementaci <xref:System.Runtime.InteropServices.ICustomMarshaler> k poskytnutí vlastního kódu zařazování.
