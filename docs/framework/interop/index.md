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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 583cfb6e3a5145c6c0dfc82ec9ff64c6d87414ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389504"
---
# <a name="interoperating-with-unmanaged-code"></a>Spolupráce s nespravovaným kódem

Rozhraní .NET Framework zvýší úroveň interakci s COM komponenty modelu COM + služby, knihovny externích typů a mnoho služeb operačního systému. Datové typy, metoda podpisy a zpracování chyb mechanismy liší mezi spravovanými a nespravovanými objektové modely. Pro zjednodušení vzájemná spolupráce mezi součástmi rozhraní .NET Framework a nespravovaného kódu a usnadňují cesty migrace, modul common language runtime ukrývá od klientů a serverů rozdíly v těchto modelů objektu.

Kód, který spouští pod kontrolou modulu runtime nazývá spravovaného kódu. Kód, který je spuštěn mimo modul runtime naopak se nazývá nespravovaného kódu. COM – součásti ActiveX rozhraní a funkcí rozhraní API Win32 jsou příklady nespravovaného kódu.

## <a name="in-this-section"></a>V tomto oddílu

[Vystavení komponent COM pro rozhraní .NET Framework](exposing-com-components.md)  
Popisuje, jak komponenty modelu COM v aplikacích rozhraní .NET Framework.

[Vystavení komponent architektury .NET Framework pro COM](exposing-dotnet-components-to-com.md)  
Popisuje způsob použití součásti rozhraní .NET Framework z aplikace modelu COM.

[Používání nespravovaných funkcí DLL](consuming-unmanaged-dll-functions.md)  
Popisuje, jak volat nespravovaný volání funkcí knihovny DLL pomocí platformy.

[Zařazování spolupráce](interop-marshaling.md)  
Popisuje zařazování pro vyvolání zprostředkovatel komunikace s objekty COM a platformu.

[Postupy: Mapování výsledků HRESULT a výjimek](how-to-map-hresults-and-exceptions.md)  
Popisuje mapování mezi výjimky a jejich hodnoty HRESULT.

[COM – obálky](com-wrappers.md)  
Popisuje obálky poskytované zprostředkovatel komunikace s objekty COM.

[Ekvivalence typů a vestavěné typy spolupráce](type-equivalence-and-embedded-interop-types.md)  
Popisuje, jak vložené informací o typu pro typy modelu COM v sestavení a určuje, jak modul common language runtime ekvivalence typů vložených COM.

[Postupy: Generování primárních sestavení vzájemné spolupráce pomocí Tlbimp.exe](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
Popisuje, jak vytvořit primární spolupracující sestavení pomocí *Tlbimp.exe* (Importér knihovny).

[Postupy: Registrace primárních sestavení spolupráce](how-to-register-primary-interop-assemblies.md)  
Popisuje postup registrace primárních sestavení vzájemné spolupráce, než je můžete odkazovat ve vašich projektů.

[Bezregistrační zprostředkovatel komunikace s objekty COM](registration-free-com-interop.md)  
Popisuje, jak zprostředkovatel komunikace s objekty COM součásti aktivovat bez použití registru systému Windows.

[Postupy: Konfigurace bezregistrační aktivace komponent využívajících rozhraní .NET Framework](configure-net-framework-based-com-components-for-reg.md)  
Popisuje postup vytvoření manifest aplikace a jak vytvořit a vložení manifestu součástí.
