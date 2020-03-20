---
title: Spolupráce s nespravovaným kódem
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
ms.openlocfilehash: 12183f390a5178f038c6dd2122a72a33e31ae0ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457966"
---
# <a name="interoperating-with-unmanaged-code"></a>Spolupráce s nespravovaným kódem

Rozhraní .NET Framework podporuje interakci s komponentami modelu COM, službami modelu COM+, externími knihovnami typů a mnoha službami operačního systému. Datové typy, podpisy metod a mechanismy zpracování chyb se liší mezi spravovanými a nespravovanými objektovými modely. Chcete-li zjednodušit vzájemné spolupráce mezi součástmi rozhraní .NET Framework a nespravovaným kódem a usnadnit cestu migrace, soubor Runtime jazyka common jazyk ukrytý chod klientů i serverů rozdíly v těchto objektových modelech.

Kód, který se spustí pod kontrolou runtime se nazývá spravovaný kód. Naopak kód, který běží mimo runtime se nazývá nespravovaný kód. Komponenty modelu COM, rozhraní ActiveX a funkce rozhraní API systému Windows jsou příklady nespravovaného kódu.

## <a name="in-this-section"></a>V tomto oddílu

[Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)  
Popisuje způsob použití komponent modelu COM z aplikací rozhraní .NET Framework.

[Vystavení komponent architektury .NET Framework pro COM](exposing-dotnet-components-to-com.md)  
Popisuje způsob použití součástí rozhraní .NET Framework z aplikací modelu COM.

[Používání nespravovaných funkcí DLL](consuming-unmanaged-dll-functions.md)  
Popisuje, jak volat nespravované funkce dll pomocí platformy vyvolat.

[Zařazování spolupráce](interop-marshaling.md)  
Popisuje zařazování pro interop com a platformy invoke.

[Postupy: Mapování výsledků HRESULT a výjimek](how-to-map-hresults-and-exceptions.md)  
Popisuje mapování mezi výjimkami a HRESULTs.

[Ekvivalence typů a vestavěné typy spolupráce](type-equivalence-and-embedded-interop-types.md)  
Popisuje, jak jsou informace o typu pro typy COM vloženy do sestavení a jak běžný jazyk runtime určuje rovnocennost vložených typů COM.

[Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
Popisuje, jak vytvořit primární interop sestavení pomocí *Tlbimp.exe* (Import knihovny typů).

[Postupy: Registrace primárních sestavení spolupráce](how-to-register-primary-interop-assemblies.md)  
Popisuje, jak zaregistrovat primární sestavení interop před odkazem na ně v projektech.

[Bezregistrační zprostředkovatel komunikace s objekty COM](registration-free-com-interop.md)  
Popisuje, jak může interop modelu COM aktivovat součásti bez použití registru systému Windows.

[Postupy: Konfigurace bezregistrační aktivace komponent využívajících rozhraní .NET Framework](configure-net-framework-based-com-components-for-reg.md)  
Popisuje, jak vytvořit manifest aplikace a jak vytvořit a vložit manifest komponenty.

## <a name="related-sections"></a>Související oddíly

[Obálky COM](../../standard/native-interop/com-wrappers.md)  
Popisuje obálky poskytované com interop.
