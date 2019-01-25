---
title: Použití atributů spolupráce
ms.date: 03/30/2017
helpviewer_keywords:
- design-time attributes
- .NET Framework, exposing components to COM
- attributes [.NET Framework], design-time functionality
- conversion-tool attributes
- attributes [.NET Framework], interop-specific
- attributes [.NET Framework], conversion-tool
- interoperation with unmanaged code, applying attributes
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
- COM interop, applying attributes
ms.assetid: b6014613-641c-4912-9e2f-83a99210a037
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 590fed6a2a4e59f438dc73057973aff4539cb1aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589763"
---
# <a name="applying-interop-attributes"></a>Použití atributů spolupráce
<xref:System.Runtime.InteropServices> Obor názvů obsahuje tři kategorie atributy specifické pro zprostředkovatele komunikace s objekty: používaných v době návrhu vámi používaných ve vzájemné spolupráce COM nástroje a rozhraní API během procesu převodu a používaných buď vy nebo komunikace s objekty COM.  
  
 Pokud nejste obeznámeni s úlohou použití atributů pro spravovaný kód, naleznete v tématu [Extending Metadata Using Attributes](../../../docs/standard/attributes/index.md). Stejně jako jiné vlastní atributy můžete použít atributy specifické pro zprostředkovatele komunikace s objekty na typy, metody, vlastnosti, parametry, polí a ostatní členy.  
  
## <a name="design-time-attributes"></a>Atributy doby návrhu  
 Můžete upravit výsledek procesu převodu prováděné COM interop nástroje a rozhraní API s použitím atributy doby návrhu. Následující tabulka popisuje atributy, které můžete použít na spravovaném zdrojovém kódu. Nástroje interoperability modelu COM, v některých případech může být také použít atributy jsou popsané v této tabulce.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.AutomationProxyAttribute>|Určuje, zda typ by měly být zařazeny pomocí zařazovací modul Automation nebo vlastní proxy server a zástupných procedur.|  
|<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>|Ovládací prvky typu vygenerované třídy rozhraní.|  
|<xref:System.Runtime.InteropServices.CoClassAttribute>|Určuje identifikátor CLSID původní coclass naimportované z knihovny typů.<br /><br /> Nástroje interoperability COM obvykle použít tento atribut.|  
|<xref:System.Runtime.InteropServices.ComImportAttribute>|Označuje, že definice coclass nebo rozhraní bylo importováno z knihovny typů COM. Modul runtime používá tento příznak k určení, jak aktivovat a zařazování typu. Tento atribut brání typu exportování zpět do knihovny typů.<br /><br /> Nástroje interoperability COM obvykle použít tento atribut.|  
|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>|Označuje, že metodu lze volat po registraci sestavení pro použití v modelu COM, tak, aby uživatelem zapsaný kód lze spustit během procesu registrace.|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|Určuje rozhraní, které jsou zdroje událostí pro třídu.<br /><br /> Nástroje interoperability COM můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>|Označuje, že by měla být volána metoda, když se registrace z modelu COM, sestavení tak, aby uživatelem zapsaný kód můžete spustit během procesu.|  
|<xref:System.Runtime.InteropServices.ComVisibleAttribute>|Vykreslí typy neviditelné do modelu COM. Pokud hodnota atributu rovná **false**. Tento atribut lze použít na jednotlivé typ nebo na celé sestavení řídit viditelnost modelu COM. Ve výchozím nastavení všechny spravované, veřejné typy jsou viditelné; atribut není potřeba zpřístupnit.|  
|<xref:System.Runtime.InteropServices.DispIdAttribute>|Určuje identifikátor odesílání modelu COM (DISPID) metodu nebo pole. Tento atribut obsahuje identifikátor DISPID pro metody, pole nebo vlastnost, kterou popisuje.<br /><br /> Nástroje interoperability COM můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.FieldOffsetAttribute>|Určuje fyzické umístění jednotlivých polí v rámci třídy při použití s **StructLayoutAttribute –** a **LayoutKind** je nastavena na hodnotu Explicit.|  
|<xref:System.Runtime.InteropServices.GuidAttribute>|Určuje třídy, rozhraní nebo celé knihovny typů globálně jedinečný identifikátor (GUID). Řetězec předán atributu musí být formátu, který je argument přijatelné konstruktor pro typ **System.Guid**.<br /><br /> Nástroje interoperability COM můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute>|Označuje, které **IDispatch** modul common language runtime používá při zpřístupňování duální rozhraní a odesílající rozhraní modelu COM. implementace rozhraní|  
|<xref:System.Runtime.InteropServices.InAttribute>|Označuje, že data by měl být zařazen do volajícímu. Slouží k parametry atributu.|  
|<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>|Určuje, jak je spravovaného rozhraní zveřejněné klientům modelu COM. (duální. odvozené rozhraní IUnknown nebo IDispatch pouze).<br /><br /> Nástroje interoperability COM můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.LCIDConversionAttribute>|Určuje, že podpis nespravované metoda očekává, že parametr LCID.<br /><br /> Nástroje interoperability COM můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.MarshalAsAttribute>|Určuje, jak data v polích nebo parametry by měly být zařazeny mezi spravovaným a nespravovaným kódem. Atribut je volitelný vždy, protože každý datový typ má výchozí chování zařazování.<br /><br /> Nástroje interoperability COM můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.OptionalAttribute>|Označuje, že parametr je nepovinný.<br /><br /> Nástroje interoperability COM můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.OutAttribute>|Označuje, že data v poli nebo parametr musí zařazovat z volaný objekt zpět na volající funkci.|  
|<xref:System.Runtime.InteropServices.PreserveSigAttribute>|Potlačí HRESULT nebo retval transformace podpisu, obvykle probíhá během volání vzájemné spolupráce. Atribut má vliv na zařazování a export knihovny typů.<br /><br /> Nástroje interoperability COM můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.ProgIdAttribute>|Určuje identifikátor ProgID třídy rozhraní .NET Framework. Slouží k tříd atributů.|  
|<xref:System.Runtime.InteropServices.StructLayoutAttribute>|Ovládací prvky, fyzické rozložení polí třídy.<br /><br /> Nástroje interoperability COM můžete použít tento atribut.|  
  
## <a name="conversion-tool-attributes"></a>Atributy převodního nástroje  
 Následující tabulka popisuje atributy, které nástroje spolupráce modelu COM použít během procesu převodu. Tyto atributy se nevztahují v době návrhu.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.ComAliasNameAttribute>|Označuje alias modelu COM pro typ parametru nebo pole. Můžete použít k parametry atributu, pole, nebo návratové hodnoty.|  
|<xref:System.Runtime.InteropServices.ComConversionLossAttribute>|Označuje, že informace o třídu nebo rozhraní se ztratí v případě, že byla importována z knihovny typů na sestavení.|  
|<xref:System.Runtime.InteropServices.ComEventInterfaceAttribute>|Určuje zdrojové rozhraní a třídy, která implementuje metodu rozhraní události.|  
|<xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>|Označuje, že sestavení bylo původně importováno z knihovny typů modelu COM. Tento atribut obsahuje definici typu knihovny původní knihovny typů.|  
|<xref:System.Runtime.InteropServices.TypeLibFuncAttribute>|Obsahuje **FUNCFLAGS** , které byly původně importovány pro tuto funkci v knihovně typů modelu COM.|  
|<xref:System.Runtime.InteropServices.TypeLibTypeAttribute>|Obsahuje **TYPEFLAGS** , které byly původně importovány pro tento typ z knihovny typů modelu COM.|  
|<xref:System.Runtime.InteropServices.TypeLibVarAttribute>|Obsahuje **VARFLAGS** , které byly původně importovány pro tuto proměnnou z knihovny typů modelu COM.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.InteropServices>
- [Vystavení komponent architektury .NET Framework pro COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Atributy](../../../docs/standard/attributes/index.md)
- [Kvalifikace typů .NET pro spolupráci](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)
- [Zabalení sestavení pro model COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
