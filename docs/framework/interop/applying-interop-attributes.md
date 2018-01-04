---
title: "Použití atributů spolupráce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea9e12140e351bb5cc2b51ac2efca8a24e94bf2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="applying-interop-attributes"></a>Použití atributů spolupráce
<xref:System.Runtime.InteropServices> Obor názvů obsahuje tři kategorie atributů specifický pro spolupráci: uplatnil v době návrhu, jaké používají vůči nástroje zprostředkovatele komunikace s objekty COM a rozhraní API během procesu převodu a jsou použita buď vy nebo zprostředkovatel komunikace s objekty COM.  
  
 Pokud jste obeznámeni s úlohy použití atributů do spravovaného kódu, najdete v části [rozšiřování metadat pomocí atributů](../../../docs/standard/attributes/index.md). Jako další vlastní atributy můžete použít specifický pro spolupráci atributy pro typy, metody, vlastnosti, parametry, pole a ostatní členové.  
  
## <a name="design-time-attributes"></a>Atributy doby návrhu  
 Můžete upravit výsledek procesu převodu provádí nástroje zprostředkovatele komunikace s objekty COM a rozhraní API pomocí atributy doby návrhu. Následující tabulka popisuje atributy, které můžete použít pro spravované zdrojového kódu. Nástroje zprostředkovatele komunikace s objekty COM, v některých případech může také použít atributy popsané v této tabulce.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.AutomationProxyAttribute>|Určuje, zda by měl být zařazen typ pomocí automatizace vláken nebo vlastní proxy server a se zakázaným inzerováním.|  
|<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>|Ovládací prvky typu vygenerované třídy rozhraní.|  
|<xref:System.Runtime.InteropServices.CoClassAttribute>|Určuje identifikátor CLSID původní třída typu coclass naimportované z knihovny typů.<br /><br /> Nástroje zprostředkovatele komunikace s objekty COM obvykle platí tento atribut.|  
|<xref:System.Runtime.InteropServices.ComImportAttribute>|Označuje, že třída typu coclass nebo rozhraní definice naimportované z knihovny typů COM. Modul runtime používá tento příznak vědět, jak aktivovat a zařazování typu. Tento atribut zakazuje typ vývozu zpět do knihovny typů.<br /><br /> Nástroje zprostředkovatele komunikace s objekty COM obvykle platí tento atribut.|  
|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>|Označuje, že metoda by měla být volána při sestavení je zaregistrovaný pro použití z modelu COM, tak, aby uživatel zapsat kód mohou být provedeny během procesu registrace.|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|Určuje rozhraní, které jsou zdroje událostí pro třídu.<br /><br /> Nástroje zprostředkovatele komunikace s objekty COM, můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>|Označuje, že metoda by měla být volána po zrušení registrace z modelu COM, sestavení tak, aby uživatel zapsat kód můžete spustit během procesu.|  
|<xref:System.Runtime.InteropServices.ComVisibleAttribute>|Vykreslí typy neviditelná do modelu COM Pokud hodnota atributu rovná **false**. Tento atribut lze použít na jednotlivé typ nebo na celé sestavení řízení COM zobrazení. Standardně jsou všechny spravované, veřejné typy viditelné; atribut není potřeba je zpřístupněte.|  
|<xref:System.Runtime.InteropServices.DispIdAttribute>|Určuje identifikátor odesílání modelu COM (DISPID) metoda nebo pole. Tento atribut obsahuje DISPID pro metodu, pole nebo vlastnost, kterou popisuje.<br /><br /> Nástroje zprostředkovatele komunikace s objekty COM, můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.FieldOffsetAttribute>|Určuje fyzické umístění každé pole v rámci třídy při použití s **StructLayoutAttribute**a **LayoutKind** je nastaven na explicitní.|  
|<xref:System.Runtime.InteropServices.GuidAttribute>|Určuje třídu, rozhraní nebo knihovny celý typ globálně jedinečný identifikátor (GUID). Musí být řetězec předán do atribut formátu, který je přípustný argument konstruktoru typu **System.Guid**.<br /><br /> Nástroje zprostředkovatele komunikace s objekty COM, můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute>|Určuje, které **IDispatch** modul common language runtime používá při vystavení duální rozhraní a odesílající rozhraní modelu COM. implementace rozhraní|  
|<xref:System.Runtime.InteropServices.InAttribute>|Označuje, že data by měl být zařazen v volajícímu. Slouží k atributu parametry.|  
|<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>|Určuje, jak je vystaven spravovaného rozhraní klientů modelu COM (duální, odvozené IUnknown, nebo jenom IDispatch).<br /><br /> Nástroje zprostředkovatele komunikace s objekty COM, můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.LCIDConversionAttribute>|Určuje, že podpisu nespravované metoda očekává parametr LCID.<br /><br /> Nástroje zprostředkovatele komunikace s objekty COM, můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.MarshalAsAttribute>|Určuje, jak by měl být zařazen data v pole nebo parametry mezi spravovanými a nespravovanými kódu. Protože každý typ dat má výchozí chování zařazování je vždy volitelný atribut.<br /><br /> Nástroje zprostředkovatele komunikace s objekty COM, můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.OptionalAttribute>|Označuje, že je volitelný parametr.<br /><br /> Nástroje zprostředkovatele komunikace s objekty COM, můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.OutAttribute>|Označuje, že data v pole nebo parametr musí být zařazen z názvem objektu zpět do jeho volajícího.|  
|<xref:System.Runtime.InteropServices.PreserveSigAttribute>|Potlačí podpis transformace HRESULT nebo retval – které obvykle probíhá během součinnosti volání. Atribut ovlivňuje zařazování a také typu Export knihovny.<br /><br /> Nástroje zprostředkovatele komunikace s objekty COM, můžete použít tento atribut.|  
|<xref:System.Runtime.InteropServices.ProgIdAttribute>|Určuje identifikátor ProgID třídy rozhraní .NET Framework. Slouží k třídy atributů.|  
|<xref:System.Runtime.InteropServices.StructLayoutAttribute>|Ovládací prvky fyzické rozložení polí třídy.<br /><br /> Nástroje zprostředkovatele komunikace s objekty COM, můžete použít tento atribut.|  
  
## <a name="conversion-tool-attributes"></a>Atributy převodního nástroje  
 Následující tabulka popisuje atributy, které během procesu převodu použít nástroje pro zprostředkovatele komunikace s objekty COM. Tyto atributy se nevztahují v době návrhu.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.ComAliasNameAttribute>|Označuje alias modelu COM, nebo parametr pole typu. Můžete použít k atributu parametry, pole, nebo návratové hodnoty.|  
|<xref:System.Runtime.InteropServices.ComConversionLossAttribute>|Označuje, že informace o třídy nebo rozhraní se ztratí v případě naimportované z knihovny typů k sestavení.|  
|<xref:System.Runtime.InteropServices.ComEventInterfaceAttribute>|Určuje zdroj rozhraní a třídy, která implementuje metodu rozhraní událostí.|  
|<xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>|Označuje, že sestavení naimportované původně z knihovny typů COM. Tento atribut obsahuje definici typu knihovny původní knihovny typů.|  
|<xref:System.Runtime.InteropServices.TypeLibFuncAttribute>|Obsahuje **FUNCFLAGS** které byly původně importovány pro tuto funkci z knihovny typů COM.|  
|<xref:System.Runtime.InteropServices.TypeLibTypeAttribute>|Obsahuje **TYPEFLAGS** které byly původně importovány pro tento typ z knihovny typů COM.|  
|<xref:System.Runtime.InteropServices.TypeLibVarAttribute>|Obsahuje **VARFLAGS** které byly původně importovány pro tuto proměnnou z knihovny typů COM.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices>  
 [Vystavení komponent architektury .NET Framework pro COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Atributy](../../../docs/standard/attributes/index.md)  
 [Kvalifikace typů .NET pro spolupráci](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)  
 [Zabalení sestavení pro model COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
