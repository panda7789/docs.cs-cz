---
title: Balení .NET Framework sestavení pro model COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df8f82605118f1af0f085aef6e76c1e4bedb2904
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69988159"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a>Balení .NET Framework sestavení pro model COM

Vývojáři modelu COM můžou těžit z následujících informací o spravovaných typech, které plánuje začlenit do své aplikace:

- Seznam typů, které mohou využívat aplikace modelu COM

  Některé spravované typy jsou pro COM neviditelné; Některé jsou viditelné, ale nelze je vytvořit. a některé jsou viditelné i vytvořitelné. Sestavení může obsahovat libovolnou kombinaci neviditelných, viditelných, nevytvořitelné a vytvořitelné typy. Pro úplnost Identifikujte typy v sestavení, které chcete zpřístupnit modelu COM, zejména v případě, že jsou tyto typy podmnožinou typů vystavených .NET Framework.

  Další informace naleznete v tématu [kvalifikační typy rozhraní .NET pro](../../standard/native-interop/qualify-net-types-for-interoperation.md)spoluprovozování.

- Pokyny pro správu verzí

  Spravované třídy, které implementují rozhraní třídy (rozhraní generované zprostředkovatelem komunikace s objekty COM), podléhají omezením správy verzí.

  Pokyny k používání rozhraní třídy naleznete v tématu [Představujeme rozhraní třídy](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).

- Pokyny k nasazení

  Sestavení se silným názvem, která jsou podepsaná vydavatelem, mohou být nainstalována do globální mezipaměti sestavení (GAC). Nepodepsaná sestavení musí být nainstalována v počítači uživatele jako soukromá sestavení.

  Další informace najdete v tématu [požadavky na zabezpečení sestavení](../app-domains/assembly-security-considerations.md).

- Zahrnutí knihovny typů

  Většina typů vyžaduje knihovnu typů, pokud je využívána aplikací modelu COM. Můžete vygenerovat knihovnu typů nebo použít tuto úlohu vývojáři modelu COM. Windows SDK poskytuje následující možnosti pro vygenerování knihovny typů:

  - [Exportér knihovny typů](#cpconpackagingassemblyforcomanchor1)

  - [TypeLibConverter – třída](#cpconpackagingassemblyforcomanchor2)

  - [Nástroj pro registraci sestavení](#cpconpackagingassemblyforcomanchor3)

  - [Nástroj pro instalaci služeb .NET](#cpconpackagingassemblyforcomanchor4)

  Bez ohledu na to, jaký mechanismus zvolíte, jsou do generované knihovny typů zahrnuty pouze veřejné typy definované v sestavení, které zadáte.

Pokyny najdete v tématu [postup: Vložte knihovny typů jako prostředky Win32 do. Aplikace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))založené na síti.

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a>knihovna typů – exportér

[Exportér knihovny typů (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md) je nástroj příkazového řádku, který převádí třídy a rozhraní obsažená v sestavení na knihovnu typů modelu COM. Jakmile jsou informace o typu třídy k dispozici, mohou klienti modelu COM vytvořit instanci třídy .NET a volat metody instance stejně, jako by šlo o objekt modelu COM. Tlbexp. exe převede v jednom okamžiku celé sestavení. Pomocí nástroje Tlbexp.exe nelze generovat informace o typu pro podtypy definované v sestavení.

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a>TypeLibConverter – třída

Třída, která je umístěna v oboru názvů **System. Runtime. Interop** , převede třídy a rozhraní obsažené v sestavení na knihovnu typů modelu COM. <xref:System.Runtime.InteropServices.TypeLibConverter> Toto rozhraní API vytváří stejné informace o typu jako Exportér knihovny typů, jak je popsáno v předchozí části.

**Třída TypeLibConverter** implementuje rozhraní <xref:System.Runtime.InteropServices.ITypeLibConverter>.

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a>Nástroj pro registraci sestavení

[Nástroj pro registraci sestavení (Regasm. exe)](../tools/regasm-exe-assembly-registration-tool.md) může generovat a registrovat knihovnu typů při použití možnosti **/TLB:** . Klienti modelu COM vyžadují, aby byly knihovny typů nainstalovány v registru systému Windows. Bez této možnosti nástroj Regasm. exe zaregistruje pouze typy v sestavení, nikoli v knihovně typů. Registrace typů v sestavení a registrace knihovny typů jsou odlišné aktivity.

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a>Nástroj pro instalaci služeb .NET

[Nástroj pro instalaci služeb .NET (Regsvcs. exe)](../tools/regsvcs-exe-net-services-installation-tool.md) přidává spravované třídy do služby komponent Windows 2000 a kombinuje několik úloh v rámci jediného nástroje. Kromě načítání a registrace sestavení může Regsvcs. exe vygenerovat, zaregistrovat a nainstalovat knihovnu typů do existující aplikace COM+ 1,0.

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [Vystavení komponent architektury .NET Framework pro COM](exposing-dotnet-components-to-com.md)
- [Kvalifikace typů .NET pro spolupráci](../../standard/native-interop/qualify-net-types-for-interoperation.md)
- [Představení rozhraní třídy](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [Důležité informace o zabezpečení sestavení](../app-domains/assembly-security-considerations.md)
- [Tlbexp.exe (exportér knihovny typů)](../tools/tlbexp-exe-type-library-exporter.md)
- [Registrování sestav pomocí modelu COM](registering-assemblies-with-com.md)
- [Postupy: Vložení knihoven typů jako prostředků Win32 do aplikací](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))
