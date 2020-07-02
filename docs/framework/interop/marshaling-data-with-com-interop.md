---
title: Zařazování dat se spoluprací COM
description: Viz články, které se týkají zařazování dat pomocí zprostředkovatele komunikace s objekty COM. Nástroje Tlbimp.exe a Tlbexp.exe převádějí mezi knihovnou typu COM a definičním sestavením.
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: eedfb60a75e2fe5fafdaa786dbb54adddf28400e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621506"
---
# <a name="marshaling-data-with-com-interop"></a>Zařazování dat se spoluprací COM
Zprostředkovatel komunikace s objekty COM poskytuje podporu jak pro použití objektů COM ze spravovaného kódu, tak pro vystavování spravovaných objektů do modelu COM. Podpora pro zařazování dat do a z modelu COM je rozsáhlá a téměř vždy poskytuje správné chování při zařazování.  
  
 Windows SDK obsahuje následující nástroje COM interop:  
  
- [Importér knihovny typů (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), který převede knihovnu typů modelu COM na definiční sestavení. Z tohoto sestavení vygeneruje služba interop marshaling obálky, které provádějí zařazování dat mezi spravovanou a nespravovanou pamětí.  
  
- [Exportér knihovny typů (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), která vytvoří knihovnu typů modelu COM ze sestavení a vygeneruje obálku, která provádí zařazování při volání metody.  
  
 Následující části odkazují na témata, která popisují procesy pro přizpůsobení obálky spolupráce, když můžete (nebo musíte) zařazovacímu programu dodat Další informace o typu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
[Postupy: ruční vytváření obálek](how-to-create-wrappers-manually.md) Popisuje, jak vytvořit obálku COM ručně ve spravovaném zdrojovém kódu.

 [Postupy: Migrace spravovaného kódu DCOM do WCF](how-to-migrate-managed-code-dcom-to-wcf.md)  
 V této části najdete popis postupu migrace spravovaného kódu DCOM do WCF pro nejbezpečnější řešení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Datové typy COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))  
 Poskytuje odpovídající spravované a nespravované datové typy.  
  
 [Přizpůsobení vydaných obálek modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))  
 V této části najdete popis postupu explicitního zařazování datových typů pomocí <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributu v době návrhu.  
  
 [Přizpůsobení obálek za běhu, které se budou volat](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))  
 Popisuje, jak upravit chování zařazování typů v definičním sestavení a jak definovat typy COM ručně.  
  
 [Pokročilá interoperabilita modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))  
 Obsahuje odkazy na Další informace o zahrnutí komponent modelu COM do aplikace .NET Framework.  
  
 [Souhrn převodu sestavení na knihovnu typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))  
 Popisuje sestavení pro proces převodu exportu knihovny typů.  
  
 [Souhrn převodu knihovny typů na sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))  
 Popisuje proces převodu knihovny typů na sestavení.  
  
 [Spolupráce pomocí obecných typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))  
 Popisuje, které akce jsou podporovány při použití obecných typů pro interoperabilitu modelu COM.
