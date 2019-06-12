---
title: Zabalení sestavení pro model COM
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
ms.openlocfilehash: 6933aa5ee253f78806aba401749256934f490126
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833598"
---
# <a name="packaging-an-assembly-for-com"></a>Zabalení sestavení pro model COM

Následující informace o spravované typy, že chtějí začlenit ve svých aplikacích využívat vývojáři COM:

- Seznam typů, které využívají aplikace modelu COM

  Některé spravované typy nejsou viditelná modelu COM; Některé jsou zobrazena, ale není vytvořitelný; a některé jsou viditelné a vytvořitelné. Sestavení může obsahovat libovolnou kombinaci typů neviditelné, není možné vytvořit, přehledné a vytvořitelné. Pro úplnost jaké typy v sestavení, které chcete vystavit rozhraní COM, zejména v případě, že tyto typy jsou podmnožinou typy, které jsou vystaveny rozhraní .NET Framework.

  Další informace najdete v tématu [kvalifikace typů .NET pro spolupráci](qualifying-net-types-for-interoperation.md).

- Správa verzí pokyny

  Spravované třídy, které implementují rozhraní třídy (rozhraní modelu COM interop generované) se vztahují omezení správy verzí.

  Pokyny k používání rozhraní, naleznete v tématu [představení rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface).

- Pokyny k nasazení

  Sestavení se silným názvem, které jsou podepsané vydavatelem je možné nainstalovat do globální mezipaměti sestavení. Nepodepsaná sestavení musí být nainstalována na počítač uživatele jako soukromá sestavení.

  Další informace najdete v tématu [důležité informace o zabezpečení sestavení](../app-domains/assembly-security-considerations.md).

- Zahrnutí knihovny typů

  Většina typů vyžadují knihovny typů při používané aplikace modelu COM. Můžete generovat knihovnu typů nebo mají vývojáři COM provedení této úlohy. Windows Software Development Kit (SDK) poskytuje následující možnosti pro vytváření knihovny typů:

  - [Exportér knihovny typů](#cpconpackagingassemblyforcomanchor1)

  - [Typelibconverter – třída](#cpconpackagingassemblyforcomanchor2)

  - [Nástroj registrace sestavení](#cpconpackagingassemblyforcomanchor3)

  - [Nástroj pro instalaci služeb .NET](#cpconpackagingassemblyforcomanchor4)

  Bez ohledu na to mechanismus, který zvolíte jsou pouze veřejné typy definované v sestavení, ve kterém zadáte součástí vygenerovanou knihovnu typů.

  Můžete zabalit jako samostatný soubor knihovny typů nebo ji vložit jako soubor prostředků Win32 v rámci. Aplikace založené na síť. Microsoft Visual Basic 6.0 provést tuto úlohu pro vás automaticky. ale při použití [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], je nutné ručně vložit vaše knihovna typů. Pokyny najdete v tématu [jak: Vložte jako prostředky systému Win32 v knihovny typů. Aplikace založené na NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a>knihovna typů – exportér

[Exportér knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) je nástroj příkazového řádku, který převede třídy a rozhraní, které jsou obsaženy v sestavení na knihovnu typů modelu COM. Jakmile je k dispozici informace o typu třídy, klientům modelu COM můžete vytvořit instance třídy .NET a volání metod instance, stejně jako by šlo objekt modelu COM. Tlbexp.exe převede celé sestavení najednou. Pomocí nástroje Tlbexp.exe nelze generovat informace o typu pro podtypy definované v sestavení.

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a>Typelibconverter – třída

<xref:System.Runtime.InteropServices.TypeLibConverter> Třídy, které jsou umístěné v **System.Runtime.Interop** převede obor názvů, třídy a rozhraní, které jsou obsaženy v sestavení na knihovnu typů modelu COM. Toto rozhraní API poskytuje stejné informace o typu jako Exportér knihovny typů, je popsáno v předchozí části.

**Typelibconverter – třída** implementuje <xref:System.Runtime.InteropServices.ITypeLibConverter>.

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a>Nástroj registrace sestavení

[Nástroj registrace sestavení (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) můžete vygenerovat a zaregistrovat knihovnu typů, při použití **/tlb:** možnost. Klienti modelu COM vyžadují instalaci knihoven typů v registru Windows. Bez této možnosti Regasm.exe pouze registruje typy v sestavení, nikoli knihovnu typů. Registrace typů v sestavení a registraci knihovny typů jsou různé aktivity.

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a>.NET Services Installation Tool

[Nástroj pro instalaci služeb .NET (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) přidá spravované třídy Služba komponent Windows 2000 a kombinuje několik úkolů v rámci jediného nástroje. Kromě načítá a registruje sestavení, Regsvcs.exe generovat, registrace a instalace do existující aplikace modelu COM + 1.0 knihovny typů.

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [Vystavení komponent architektury .NET Framework pro COM](exposing-dotnet-components-to-com.md)
- [Kvalifikace typů .NET pro spolupráci](qualifying-net-types-for-interoperation.md)
- [Představení rozhraní třídy](com-callable-wrapper.md#introducing-the-class-interface)
- [Důležité informace o zabezpečení sestavení](../app-domains/assembly-security-considerations.md)
- [Tlbexp.exe (exportér knihovny typů)](../tools/tlbexp-exe-type-library-exporter.md)
- [Registrování sestav pomocí modelu COM](registering-assemblies-with-com.md)
- [Postupy: Knihovny typů vkládání jako prostředky systému Win32 do aplikací](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))
