---
title: Vystavení součástí .NET pro COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db4380e97cf4d556248f42981b350160710f1dd8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051822"
---
# <a name="exposing-net-components-to-com"></a>Vystavení součástí .NET pro COM

Zápis typu rozhraní .NET a využití tohoto typu z nespravovaného kódu jsou odlišné aktivity pro vývojáře. Tato část popisuje několik tipů pro psaní spravovaného kódu, který spolupracuje s klienty modelu COM:

- [Kvalifikování typů .NET pro](../../standard/native-interop/qualify-net-types-for-interoperation.md)spoluprovozování.

     Všechny spravované typy, metody, vlastnosti, pole a události, které chcete zveřejnit pro model COM, musí být veřejné. Typy musí mít veřejný konstruktor bez parametrů, který je jediným konstruktorem, který lze vyvolat pomocí modelu COM.

- [Použití atributů spolupráce](../../standard/native-interop/apply-interop-attributes.md)

     Vlastní atributy v rámci spravovaného kódu mohou zlepšit interoperabilitu komponenty.

- [Balení sestavení pro model COM](packaging-an-assembly-for-com.md).

     Vývojáři modelu COM mohou vyžadovat, aby byly shrnuty kroky při odkazování a nasazení vašich sestavení.

 Kromě toho tato část identifikuje úlohy týkající se využívání spravovaného typu z klienta modelu COM.

## <a name="to-consume-a-managed-type-from-com"></a>Využití spravovaného typu z modelu COM

1. [Registrovat sestavení pomocí modelu COM](registering-assemblies-with-com.md).

     Typy v sestavení (a knihovnách typů) musí být registrovány v době návrhu. Pokud instalační program neregistruje sestavení, dejte vývojářům modelu COM pokyn, aby používal nástroj Regasm. exe.

2. [Odkazování na typy .NET z modelu COM](how-to-reference-net-types-from-com.md).

     Vývojáři modelu COM mohou odkazovat na typy v sestavení pomocí stejných nástrojů a technik, které dnes používají.

3. [Zavolejte objekt .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).

     Vývojáři modelu COM mohou volat metody objektu .NET stejným způsobem jako volání metod na jakýkoli nespravovaný typ. Například rozhraní API pro technologii COM **CoCreateInstance** aktivuje objekty .NET.

4. [Nasaďte aplikaci pro přístup k modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).

     Sestavení se silným názvem může být nainstalováno v globální mezipaměti sestavení (GAC) a vyžaduje podpis od jeho vydavatele. Sestavení, která nemají silný název, musí být nainstalována v adresáři aplikace klienta.

## <a name="see-also"></a>Viz také:

- [Spolupráce s nespravovaným kódem](index.md)
- [Ukázka zprostředkovatele komunikace s objekty COM: Klient COM a Server .NET](com-interop-sample-com-client-and-net-server.md)
