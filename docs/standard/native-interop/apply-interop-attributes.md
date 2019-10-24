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
ms.openlocfilehash: 5c0b3c9d13267abe50ee187bce0c56485be29613
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775286"
---
# <a name="applying-interop-attributes"></a>Použití atributů spolupráce
Obor názvů <xref:System.Runtime.InteropServices> poskytuje tři kategorie atributů specifických pro spolupráci: ty, které jste použili v době návrhu, ty, které byly aplikovány pomocí nástrojů pro spolupráci s objekty COM a rozhraní API během procesu převodu a které byly aplikovány vámi nebo zprostředkovatelem komunikace s objekty COM.  
  
 Pokud nejste obeznámeni s úlohou použití atributů pro spravovaný kód, přečtěte si téma [rozšíření metadat pomocí atributů](../../../docs/standard/attributes/index.md). Podobně jako u jiných vlastních atributů můžete použít atributy specifické pro spolupráci na typy, metody, vlastnosti, parametry, pole a další členy.  
  
## <a name="design-time-attributes"></a>Atributy doby návrhu  
 Můžete upravit výsledek procesu převodu prováděného pomocí nástrojů pro spolupráci s objekty COM a rozhraní API pomocí atributů pro dobu návrhu. Následující tabulka popisuje atributy, které lze použít pro spravovaný zdrojový kód. Nástroje pro vzájemné spolupráce modelu COM mohou také použít atributy popsané v této tabulce.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.AutomationProxyAttribute>|Určuje, zda má být typ zařazen pomocí zařazovacího modulu automatizace nebo vlastního proxy a zástupné procedury.|  
|<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>|Řídí typ rozhraní generovaného pro třídu.|  
|<xref:System.Runtime.InteropServices.CoClassAttribute>|Určuje identifikátor CLSID původní coclass importované z knihovny typů.<br /><br /> Nástroje zprostředkovatele komunikace s objekty COM obvykle používají tento atribut.|  
|<xref:System.Runtime.InteropServices.ComImportAttribute>|Označuje, že definice typu coclass nebo rozhraní byla naimportována z knihovny typů modelu COM. Modul runtime pomocí tohoto příznaku informuje o tom, jak typ aktivovat a zařadit. Tento atribut zakazuje export typu zpět do knihovny typů.<br /><br /> Nástroje zprostředkovatele komunikace s objekty COM obvykle používají tento atribut.|  
|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>|Označuje, že metoda by měla být volána, když je sestavení registrováno pro použití z modelu COM, aby bylo možné během procesu registrace spustit uživatelsky psaný kód.|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|Označuje rozhraní, která jsou zdrojem událostí pro třídu.<br /><br /> Nástroje pro spolupráci s objekty COM mohou použít tento atribut.|  
|<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>|Označuje, že metoda by měla být volána, když je zrušena registrace sestavení z modelu COM, aby mohl být během procesu proveden uživatelsky napsaný kód.|  
|<xref:System.Runtime.InteropServices.ComVisibleAttribute>|Pokud se hodnota atributu rovná **false**, vykresluje se typy neviditelné na com. Tento atribut lze použít na jednotlivý typ nebo na celé sestavení pro řízení viditelnosti modelu COM. Ve výchozím nastavení jsou viditelné všechny spravované, veřejné typy. atribut není nutné, aby jej bylo možné zobrazit.|  
|<xref:System.Runtime.InteropServices.DispIdAttribute>|Určuje identifikátor odeslání objektu COM (DISPID) metody nebo pole. Tento atribut obsahuje identifikátor DISPID pro metodu, pole nebo vlastnost, kterou popisuje.<br /><br /> Nástroje pro spolupráci s objekty COM mohou použít tento atribut.| 
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute>|Označuje výchozí rozhraní pro třídu COM implementovanou v rozhraní .NET.<br /><br /> Nástroje pro spolupráci s objekty COM mohou použít tento atribut.|
|<xref:System.Runtime.InteropServices.FieldOffsetAttribute>|Označuje fyzickou pozici každého pole v rámci třídy při použití s **StructLayoutAttribute**a **LayoutKind** je nastaven na hodnotu Explicit.|  
|<xref:System.Runtime.InteropServices.GuidAttribute>|Určuje globálně jedinečný identifikátor (GUID) třídy, rozhraní nebo celé knihovny typů. Řetězec předaný atributu musí být formát, který je přijatelným argumentem konstruktoru pro typ **System. GUID**.<br /><br /> Nástroje pro spolupráci s objekty COM mohou použít tento atribut.|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute>|Určuje, která implementace rozhraní **IDispatch** používá modul CLR při vystavování duálních rozhraní a IDispatch do modelu COM.|  
|<xref:System.Runtime.InteropServices.InAttribute>|Označuje, že data by měla být zařazena do volajícího. Dá se použít k parametrům atributů.|  
|<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>|Řídí způsob zpřístupnění spravovaného rozhraní klientům modelu COM (pouze duální, IUnknown-odvozený nebo IDispatch).<br /><br /> Nástroje pro spolupráci s objekty COM mohou použít tento atribut.|  
|<xref:System.Runtime.InteropServices.LCIDConversionAttribute>|Označuje, že signatura nespravované metody očekává parametr LCID.<br /><br /> Nástroje pro spolupráci s objekty COM mohou použít tento atribut.|  
|<xref:System.Runtime.InteropServices.MarshalAsAttribute>|Určuje, jak mají být data v polích nebo parametrech zařazena mezi spravovaný a nespravovaný kód. Atribut je vždy volitelný, protože každý datový typ má výchozí chování zařazování.<br /><br /> Nástroje pro spolupráci s objekty COM mohou použít tento atribut.|  
|<xref:System.Runtime.InteropServices.OptionalAttribute>|Označuje, že parametr je nepovinný.<br /><br /> Nástroje pro spolupráci s objekty COM mohou použít tento atribut.|  
|<xref:System.Runtime.InteropServices.OutAttribute>|Označuje, že data v poli nebo parametru musí být zařazena z pojmenovaného objektu zpět na jeho volajícího.|  
|<xref:System.Runtime.InteropServices.PreserveSigAttribute>|Potlačí transformaci signatury HRESULT nebo retval, která obvykle probíhá během volání meziprovozu. Atribut ovlivňuje zařazování i export knihovny typů.<br /><br /> Nástroje pro spolupráci s objekty COM mohou použít tento atribut.|  
|<xref:System.Runtime.InteropServices.ProgIdAttribute>|Určuje identifikátor ProgID .NET Framework třídy. Lze použít pro třídy atributů.|  
|<xref:System.Runtime.InteropServices.StructLayoutAttribute>|Ovládá fyzické rozložení polí třídy.<br /><br /> Nástroje pro spolupráci s objekty COM mohou použít tento atribut.|  
  
## <a name="conversion-tool-attributes"></a>Atributy nástroje pro převod  
 Následující tabulka popisuje atributy, které se během procesu převodu vztahují na nástroje COM interop Tools. Tyto atributy nepoužijete v době návrhu.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.ComAliasNameAttribute>|Označuje alias COM pro parametr nebo typ pole. Dá se použít k parametrům atributů, polím nebo návratovým hodnotám.|  
|<xref:System.Runtime.InteropServices.ComConversionLossAttribute>|Označuje, že informace o třídě nebo rozhraní byly při importu z knihovny typů do sestavení ztraceny.|  
|<xref:System.Runtime.InteropServices.ComEventInterfaceAttribute>|Identifikuje zdrojové rozhraní a třídu, která implementuje metody rozhraní události.|  
|<xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>|Označuje, že bylo sestavení původně importováno z knihovny typů modelu COM. Tento atribut obsahuje definici knihovny typů původní knihovny typů.|  
|<xref:System.Runtime.InteropServices.TypeLibFuncAttribute>|Obsahuje **FUNCFLAGS** , které byly původně importovány pro tuto funkci z knihovny typů modelu COM.|  
|<xref:System.Runtime.InteropServices.TypeLibTypeAttribute>|Obsahuje **TYPEFLAGS** , které byly původně importovány pro tento typ z knihovny typů modelu COM.|  
|<xref:System.Runtime.InteropServices.TypeLibVarAttribute>|Obsahuje **VARFLAGS** , které byly původně importovány pro tuto proměnnou z knihovny typů modelu COM.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices>
- [Vystavení komponent architektury .NET Framework pro COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Atributy](../../../docs/standard/attributes/index.md)
- [Kvalifikace typů .NET pro spolupráci](../../../docs/standard/native-interop/qualify-net-types-for-interoperation.md)
- [Balení .NET Framework sestavení pro model COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
