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
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457966"
---
# <a name="interoperating-with-unmanaged-code"></a>Spolupráce s nespravovaným kódem

.NET Framework podporuje interakci s komponentami COM, službami COM+, externími knihovnami typů a mnoha službami operačního systému. Datové typy, signatury metod a mechanismy zpracování chyb se liší mezi spravovanými a nespravovanými objektovými modely. Aby bylo možné zjednodušit vzájemnou spolupráci mezi .NET Framework komponentami a nespravovaným kódem, a usnadnit tak cestu migrace, modul CLR (Common Language Runtime) se v těchto objektových modelech skrývá mezi klienty a servery.

Kód, který se spouští pod ovládacím prvkem modulu runtime, se nazývá spravovaný kód. Naopak kód, který se spouští mimo modul runtime, se nazývá nespravovaný kód. Mezi příklady nespravovaného kódu patří komponenty modelu COM, rozhraní ActiveX a funkce rozhraní API systému Windows.

## <a name="in-this-section"></a>V tomto oddílu

[Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)  
Popisuje, jak použít komponenty modelu COM z aplikace .NET Framework.

[Vystavení komponent architektury .NET Framework pro COM](exposing-dotnet-components-to-com.md)  
Popisuje, jak používat .NET Framework komponenty z aplikací modelu COM.

[Používání nespravovaných funkcí DLL](consuming-unmanaged-dll-functions.md)  
Popisuje, jak volat nespravované funkce knihovny DLL pomocí vyvolání platformy.

[Zařazování spolupráce](interop-marshaling.md)  
Popisuje zařazování pro zprostředkovatele komunikace s objekty COM a vyvolání platformy.

[Postupy: Mapování výsledků HRESULT a výjimek](how-to-map-hresults-and-exceptions.md)  
Popisuje mapování mezi výjimkami a HRESULTs.

[Ekvivalence typů a vestavěné typy spolupráce](type-equivalence-and-embedded-interop-types.md)  
Popisuje způsob vložení informací o typu pro typy modelu COM do sestavení a jak modul CLR (Common Language Runtime) určí rovnocennost integrovaných typů COM.

[Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
Popisuje, jak vypracovávat primární spolupracující sestavení pomocí nástroje *Tlbimp. exe* (importér knihovny typů).

[Postupy: Registrace primárních sestavení spolupráce](how-to-register-primary-interop-assemblies.md)  
Popisuje, jak registrovat primární sestavení vzájemné spolupráce předtím, než na ně můžete odkazovat v projektech.

[Bezregistrační zprostředkovatel komunikace s objekty COM](registration-free-com-interop.md)  
Popisuje, jak může zprostředkovatel komunikace s objekty COM aktivovat součásti bez použití registru systému Windows.

[Postupy: Konfigurace bezregistrační aktivace komponent využívajících rozhraní .NET Framework](configure-net-framework-based-com-components-for-reg.md)  
Popisuje, jak vytvořit manifest aplikace a jak vytvořit a vložit manifest součásti.

## <a name="related-sections"></a>Související oddíly

[COM – obálky](../../standard/native-interop/com-wrappers.md)  
Popisuje obálky poskytované zprostředkovatelem komunikace s objekty COM.
