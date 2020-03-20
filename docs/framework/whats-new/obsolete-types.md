---
title: Zastaralé typy v rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, obsolete types
- types, obsolete in .NET Framework 4.5
- obsolete types [.NET Framework]
ms.assetid: e636d024-0fac-45eb-b721-25a8c0ceca8f
ms.openlocfilehash: b7932a553f39e1f1da2a3946878d6224099da8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802684"
---
# <a name="obsolete-types-in-the-net-framework"></a>Zastaralé typy v rozhraní .NET Framework

<a name="introduction"></a>Tabulky v tomto článku seznam typů, které jsou zastaralé v rozhraní .NET Framework 4.5 a .NET Framework 4.6, uspořádané podle sestavení. Pomocí následujících odkazů zobrazíte seznam zastaralých typů a doporučené alternativy v každé sestavě. Protože tyto typy jsou zastaralé, všechny jejich členy jsou také zastaralé. Seznam dalších zastaralých členů v knihovně tříd rozhraní .NET Framework naleznete v [tématu Zastaralé členy](obsolete-members.md).

- [Zastaralé typy v systémových sestavách](#obsolete_types_in_system_assemblies)

  - [mscorlib.dll](#mscorlib)

  - [System.Core.dll](#Core)

  - [System.Data.dll](#data)

  - [System.Data.OracleClient.dll](#oracleclient)

  - [Soubor System.Design.dll](#design)

  - [System.dll](#system)

  - [System.EnterpriseServices.dll](#enterpriseservices)

  - [System.Net.dll](#net)

  - [System.ServiceModel.dll](#servicemodel)

  - [Soubor System.Web.dll](#web)

  - [Soubor System.Web.Mobile.dll](#mobile)

  - [Soubor System.Workflow.Activities.dll](#workflow_activities)

  - [Soubor System.Workflow.ComponentModel.dll](#workflow_componentmodel)

  - [Soubor System.Workflow.Runtime.dll](#workflow_runtime)

  - [Soubor System.WorkflowServices.dll](#workflowservices)

  - [Soubor System.Xaml.dll](#xaml)

  - [System.Xml.dll](#xml)

  - [Soubor WindowsBase.dll](#WindowsBase)

- [Zastaralé typy v sestaveních microsoftu](#obsolete_types_in_microsoft_assemblies)

  - [Soubor IEHost.dll a IEExec.exe](#IEHost)

  - [Soubor Microsoft.Build.Engine.dll](#Engine)

  - [Soubor Microsoft.JScript.dll](#jscript)

  - [Soubor Microsoft.VisualBasic.Compatibility.dll](#VBCompat)

  - [Soubor Microsoft.VisualBasic.Compatibility.Data.dll](#VBCompatData)

  - [Soubor Microsoft.VisualC.dll](#visualc)

<a name="obsolete_types_in_system_assemblies"></a>

## <a name="obsolete-types-in-system-assemblies"></a>Zastaralé typy v systémových sestavách

V následujících tabulkách jsou uvedeny typy, které byly v systémových sestaveních deklarovány jako zastaralé. Tato sestavení se používají\-pro vývoj aplikací pro obecné účely, který se zaměřuje na rozhraní .NET Framework.

<a name="mscorlib"></a>

### <a name="assembly-mscorlibdll"></a>Sestava: mscorlib.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.ExecutionEngineException?displayProperty=nameWithType>|Tento typ dříve indikoval nespecifikovanou závažnou chybu v době běhu. Runtime již vyvolá tuto výjimku, takže tento typ je zastaralý.|
|<xref:System.Collections.CaseInsensitiveHashCodeProvider?displayProperty=nameWithType>|Použijte <xref:System.StringComparer?displayProperty=nameWithType> místo toho.|
|<xref:System.Collections.IHashCodeProvider?displayProperty=nameWithType>|Použijte <xref:System.Collections.IEqualityComparer?displayProperty=nameWithType> místo toho.|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|Třída <xref:System.Configuration.Assemblies.AssemblyHash> byla zastaralá.|
|<xref:System.Diagnostics.Contracts.Internal.ContractHelper?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5. Místo <xref:System.Runtime.CompilerServices.ContractHelper?displayProperty=nameWithType> toho použijte třídu v oboru názvů System.Runtime.CompilerServices.|
|<xref:System.Reflection.Emit.UnmanagedMarshal?displayProperty=nameWithType>|Alternativní rozhraní API je k <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> dispozici: Místo toho vyzařujte vlastní atribut.|
|<xref:System.Runtime.InteropServices.BIND_OPTS?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.BIND_OPTS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.BINDPTR?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.BINDPTR?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.CALLCONV?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.CALLCONV?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.CONNECTDATA?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.CONNECTDATA?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.DESCKIND?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.DESCKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.DISPPARAMS?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.DISPPARAMS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.ELEMDESC?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.ELEMDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.EXCEPINFO?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.EXCEPINFO?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FILETIME?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.FILETIME?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FUNCDESC?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.FUNCDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FUNCFLAGS?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.FUNCFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FUNCKIND?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.FUNCKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType>|Tento atribut je zastaralé a budou odebrány v budoucí verzi.|
|<xref:System.Runtime.InteropServices.IDispatchImplType?displayProperty=nameWithType>|Je <xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType> zastaralé.|
|<xref:System.Runtime.InteropServices.IDLDESC?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IDLDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.IDLFLAG?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IDLFLAG?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.IMPLTYPEFLAGS?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IMPLTYPEFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.INVOKEKIND?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.INVOKEKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.LIBFLAGS?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.LIBFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.PARAMDESC?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.PARAMDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.PARAMFLAG?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.PARAMFLAG?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.SetWin32ContextInIDispatchAttribute?displayProperty=nameWithType>|Tento atribut byl zastaral. Domény aplikací již nerespektují hranice kontextu aktivace ve voláníi IDispatch.|
|<xref:System.Runtime.InteropServices.STATSTG?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.STATSTG?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.SYSKIND?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.SYSKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEATTR?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.TYPEATTR?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEDESC?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.TYPEDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEFLAGS?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.TYPEFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEKIND?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.TYPEKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPELIBATTR?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.TYPELIBATTR?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIBindCtx?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IBindCtx?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPoint?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPointContainer?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnectionPoints?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IEnumConnectionPoints?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnections?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IEnumConnections?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumMoniker?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IEnumMoniker?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumString?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IEnumString?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumVARIANT?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIMoniker?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IMoniker?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIPersistFile?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IPersistFile?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIRunningObjectTable?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IRunningObjectTable?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIStream?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMITypeComp?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.ITypeComp?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMITypeInfo?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMITypeLib?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.ITypeLib?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.VARDESC?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.VARDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.VARFLAGS?displayProperty=nameWithType>|Místo toho použijte <xref:System.Runtime.InteropServices.ComTypes.VARFLAGS?displayProperty=nameWithType>.|
|<xref:System.Security.SecurityCriticalScope?displayProperty=nameWithType>|<xref:System.Security.SecurityCriticalScope>se používá pouze pro kompatibilitu průhlednosti rozhraní .NET 2.0.|
|<xref:System.Security.SecurityTreatAsSafeAttribute?displayProperty=nameWithType>|<xref:System.Security.SecurityTreatAsSafeAttribute>se používá pouze pro kompatibilitu průhlednosti rozhraní .NET 2.0. Použijte <xref:System.Security.SecuritySafeCriticalAttribute?displayProperty=nameWithType> místo.|
|<xref:System.Security.Policy.FirstMatchCodeGroup?displayProperty=nameWithType>|Tento typ je zastaralý a bude odebrán v budoucí verzi rozhraní .NET Framework.|
|<xref:System.Security.Policy.PermissionRequestEvidence?displayProperty=nameWithType>|Deklarativní zabezpečení na úrovni sestavení je zastaralé a ve výchozím nastavení již není vynuceno clr.|
|<xref:System.Security.Policy.UnionCodeGroup?displayProperty=nameWithType>|Tento typ je zastaralý a bude odebrán v budoucí verzi rozhraní .NET Framework.|

[Zpět na začátek](#introduction)

<a name="Core"></a>

### <a name="assembly-systemcoredll"></a>Sestava: System.Core.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Runtime.CompilerServices.ExecutionScope?displayProperty=nameWithType>|Použití tohoto typu generuje chybu kompilátoru.<br /><br /> Nepoužívejte tento typ.|

[Zpět na začátek](#introduction)

<a name="data"></a>

### <a name="assembly-systemdatadll"></a>Sestava: System.Data.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=nameWithType>|<xref:System.Data.DataSysDescriptionAttribute>byla zastaralá.|
|<xref:System.Data.PropertyAttributes?displayProperty=nameWithType>|<xref:System.Data.PropertyAttributes>byla zastaralá.|
|<xref:System.Data.TypedDataSetGenerator?displayProperty=nameWithType>|Třída <xref:System.Data.TypedDataSetGenerator> bude odebrána v budoucí verzi. Použijte <xref:System.Data.Design.TypedDataSetGenerator?displayProperty=nameWithType> prosím v souboru System.Design.dll.|
|<xref:System.Xml.XmlDataDocument?displayProperty=nameWithType>|Třída <xref:System.Xml.XmlDataDocument> bude odebrána v budoucí verzi.|

[Zpět na začátek](#introduction)

<a name="oracleclient"></a>

### <a name="assembly-systemdataoracleclientdll"></a>Sestava: System.Data.OracleClient.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Data.OracleClient.OracleClientFactory?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleClientFactory>byla zastaralá.|
|<xref:System.Data.OracleClient.OracleCommand?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommand>byla zastaralá.|
|<xref:System.Data.OracleClient.OracleCommandBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommandBuilder>byla zastaralá.|
|<xref:System.Data.OracleClient.OracleConnection?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnection>byla zastaralá.|
|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder>byla zastaralá.|
|<xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleDataAdapter>byla zastaralá.|
|<xref:System.Data.OracleClient.OraclePermission?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermission>byla zastaralá.|
|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType>byla zastaralá.|

[Zpět na začátek](#introduction)

<a name="design"></a>

### <a name="assembly-systemdesigndll"></a>Sestava: System.Design.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.ComponentModel.Design.LocalizationExtenderProvider?displayProperty=nameWithType>|Tato třída byla zastaralá. Místo toho použijte <xref:System.ComponentModel.Design.Serialization.CodeDomLocalizationProvider?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.DataBindingCollectionConverter?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože databindings <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> úpravy se spustí prostřednictvím místo mřížky vlastností.|
|<xref:System.Web.UI.Design.DataBindingCollectionEditor?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože databindings <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> úpravy se spustí prostřednictvím místo mřížky vlastností.|
|<xref:System.Web.UI.Design.IControlDesignerBehavior?displayProperty=nameWithType>|Doporučená alternativa je <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> a <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IHtmlControlDesignerBehavior?displayProperty=nameWithType>|Doporučená alternativa je <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> a <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ITemplateEditingFrame?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože úpravy šablony jsou zpracovány v . <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> Chcete-li podporovat úpravy šablony, <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> zpřístupní data šablony ve vlastnosti a volejte <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IWebFormReferenceManager?displayProperty=nameWithType>|Doporučená alternativa je <xref:System.Web.UI.Design.WebFormsReferenceManager?displayProperty=nameWithType>. Obsahuje <xref:System.Web.UI.Design.WebFormsReferenceManager> další funkce a umožňuje větší rozšiřitelnost. Chcete-li <xref:System.Web.UI.Design.WebFormsReferenceManager>získat `RootDesigner.ReferenceManager` , použijte <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>vlastnost z vašeho .|
|<xref:System.Web.UI.Design.IWebFormsDocumentService?displayProperty=nameWithType>|Doporučená alternativa je <xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=nameWithType>. Obsahuje <xref:System.Web.UI.Design.WebFormsRootDesigner> další funkce a umožňuje větší rozšiřitelnost. Chcete-li <xref:System.Web.UI.Design.WebFormsRootDesigner>získat <xref:System.Web.UI.Design.ControlDesigner.RootDesigner%2A> , použijte <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>vlastnost z vašeho .|
|<xref:System.Web.UI.Design.ITemplateEditingService?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože úpravy šablony jsou zpracovány v . <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> Chcete-li podporovat úpravy šablony, <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> zpřístupní data šablony ve vlastnosti a volejte <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ReadWriteControlDesigner?displayProperty=nameWithType>|Doporučenou alternativou <xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=nameWithType> <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> je, protože používá pro úpravy obsahu. Oblasti návrháře umožňují lepší kontrolu upraveného obsahu.|
|<xref:System.Web.UI.Design.TemplateEditingService?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože úpravy šablony jsou zpracovány v . <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> Chcete-li podporovat úpravy šablony, <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> zpřístupní data šablony ve vlastnosti a volejte <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.TemplateEditingVerb?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože úpravy šablony jsou zpracovány v . <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> Chcete-li podporovat úpravy šablony, <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> zpřístupní data šablony ve vlastnosti a volejte <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.WebControls.CalendarAutoFormatDialog?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože dialogové okno Automatické formátování spouštěje hostitel návrháře. Seznam dostupných automatických formátů <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> je <xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=nameWithType> vystaven na vlastnosti.|
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=nameWithType>|Doporučenou alternativou <xref:System.Web.UI.Design.WebControls.PanelContainerDesigner?displayProperty=nameWithType> <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> je, protože používá pro úpravy obsahu. Oblasti návrháře umožňují lepší kontrolu upraveného obsahu.|

[Zpět na začátek](#introduction)

<a name="system"></a>

### <a name="assembly-systemdll"></a>Sestava: System.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.ComponentModel.IComNativeDescriptorHandler?displayProperty=nameWithType>|Toto rozhraní bylo zastaralé. <xref:System.ComponentModel.TypeDescriptionProvider?displayProperty=nameWithType> Místo toho přidejte typ <xref:System.ComponentModel.TypeDescriptor.ComObjectType%2A?displayProperty=nameWithType> popisovače.|
|<xref:System.ComponentModel.RecommendedAsConfigurableAttribute?displayProperty=nameWithType>|Místo <xref:System.ComponentModel.SettingsBindableAttribute?displayProperty=nameWithType> toho můžete pracovat s novým modelem nastavení.|
|<xref:System.ComponentModel.Design.Serialization.RootDesignerSerializerAttribute?displayProperty=nameWithType>|Tento atribut byl zastaral. Místo toho použijte <xref:System.ComponentModel.Design.Serialization.DesignerSerializerAttribute?displayProperty=nameWithType>.|
|<xref:System.Diagnostics.DiagnosticsConfigurationHandler?displayProperty=nameWithType>|Tato třída byla zastaralá.|
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=nameWithType>|Tato třída byla zastaralá. Místo toho použijte čítače <xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType> výkonu prostřednictvím třídy.|
|<xref:System.Net.GlobalProxySelection?displayProperty=nameWithType>|Tato třída byla zastaralá. Místo <xref:System.Net.WebRequest.DefaultWebProxy%2A?displayProperty=nameWithType> toho použijte přístup k globálnímu výchozímu proxy serveru a nastavte jej. Místo . <xref:System.Net.GlobalProxySelection.GetEmptyWebProxy%2A?displayProperty=nameWithType>|
|<xref:System.Net.Sockets.SocketClientAccessPolicyProtocol?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu generuje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|

[Zpět na začátek](#introduction)

<a name="enterpriseservices"></a>

### <a name="assembly-systementerpriseservicesdll"></a>Sestavení: System.EnterpriseServices.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.EnterpriseServices.RegistrationHelperTx?displayProperty=nameWithType>|Třída <xref:System.EnterpriseServices.RegistrationHelperTx> byla zastaralá.|

[Zpět na začátek](#introduction)

<a name="net"></a>

### <a name="assembly-systemnetdll"></a>Sestava: System.Net.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Net.INetworkProgress?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu generuje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.IUnsafeWebRequestCreate?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu generuje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.NetworkProgressChangedEventArgs?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu generuje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.UiSynchronizationContext?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu generuje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.Sockets.HttpPolicyDownloaderProtocol?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu generuje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.Sockets.SecurityCriticalAction?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu generuje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.Sockets.SocketPolicy?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu generuje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.Sockets.UdpAnySourceMulticastClient?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu generuje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.Sockets.UdpSingleSourceMulticastClient?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu generuje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|

[Zpět na začátek](#introduction)

<a name="servicemodel"></a>

### <a name="assembly-systemservicemodeldll"></a>Sestava: System.ServiceModel.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.ServiceModel.NetPeerTcpBinding?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkce kanálu peer je zastaralá a bude v budoucnu odebrána.|
|<xref:System.ServiceModel.Channels.HttpCookieContainerBindingElement?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Tento typ je zastaralý. Chcete-li <xref:System.Net.CookieContainer>povolit `AllowCookies` protokol Http , použijte <xref:System.ServiceModel.Channels.HttpTransportBindingElement>vlastnost na vazbě Http nebo na .|
|<xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkce kanálu peer je zastaralá a bude v budoucnu odebrána.|
|<xref:System.ServiceModel.Channels.PeerTransportBindingElement?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkce kanálu peer je zastaralá a bude v budoucnu odebrána.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingCollectionElement?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkce kanálu peer je zastaralá a bude v budoucnu odebrána.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkce kanálu peer je zastaralá a bude v budoucnu odebrána.|
|<xref:System.ServiceModel.Configuration.PeerTransportElement?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkce kanálu peer je zastaralá a bude v budoucnu odebrána.|
|<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkce kanálu peer je zastaralá a bude v budoucnu odebrána.|

[Zpět na začátek](#introduction)

<a name="web"></a>

### <a name="assembly-systemwebdll"></a>Sestava: System.Web.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Web.Configuration.PassportAuthentication?displayProperty=nameWithType>|Tento typ je zastaralý. Ověřovací produkt služby Passport již není podporován a byl nahrazen [účtem Microsoft.](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Mail.MailAttachment?displayProperty=nameWithType>|Doporučená alternativa je <xref:System.Net.Mail.Attachment?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailEncoding?displayProperty=nameWithType>|Doporučená alternativa je <xref:System.Net.Mime.TransferEncoding?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailFormat?displayProperty=nameWithType>|Doporučená alternativa je <xref:System.Net.Mail.MailMessage.IsBodyHtml%2A?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>|Doporučená alternativa je <xref:System.Net.Mail.MailMessage?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailPriority?displayProperty=nameWithType>|Doporučená alternativa je <xref:System.Net.Mail.MailPriority?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.SmtpMail?displayProperty=nameWithType>|Doporučená alternativa je <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>.|
|<xref:System.Web.Security.PassportAuthenticationEventArgs?displayProperty=nameWithType>|Tento typ je zastaralý. Ověřovací produkt služby Passport již není podporován a byl nahrazen [účtem Microsoft.](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Security.PassportAuthenticationEventHandler?displayProperty=nameWithType>|Tento typ je zastaralý. Ověřovací produkt služby Passport již není podporován a byl nahrazen [účtem Microsoft.](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Security.PassportAuthenticationModule?displayProperty=nameWithType>|Tento typ je zastaralý. Ověřovací produkt služby Passport již není podporován a byl nahrazen [účtem Microsoft.](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Security.PassportIdentity?displayProperty=nameWithType>|Tento typ je zastaralý. Ověřovací produkt služby Passport již není podporován a byl nahrazen [účtem Microsoft.](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Security.PassportPrincipal?displayProperty=nameWithType>|Tento typ je zastaralý. Ověřovací produkt služby Passport již není podporován a byl nahrazen [účtem Microsoft.](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.UI.ObjectConverter?displayProperty=nameWithType>|Doporučená alternativa je <xref:System.Convert?displayProperty=nameWithType> a <xref:System.String.Format%2A?displayProperty=nameWithType>.|

[Zpět na začátek](#introduction)

<a name="mobile"></a>

### <a name="assembly-systemwebmobiledll"></a>Sestava: System.Web.Mobile.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Web.Mobile.CookielessData?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.DeviceFilterElement?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.DeviceFilterElementCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.DeviceFiltersSection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.ErrorHandlerModule?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileCapabilities?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileDeviceCapabilitiesSectionHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileErrorInfo?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileFormsAuthentication?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.IMobileDesigner?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.IMobileWebFormServices?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.MobileResource?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataFieldConverter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataMemberConverter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.AdRotator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Alignment?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ArrayListCollectionBase?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.BaseValidator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.BooleanOption?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Calendar?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Command?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.CommandFormat?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.CompareValidator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Constants?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ControlElement?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ControlElementCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ControlPager?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.CustomValidator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DesignerAdapterAttribute?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceElement?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceElementCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceOverridableAttribute?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecific?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoice?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateContainer?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ErrorFormatterPage?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FontInfo?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FontSize?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Form?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FormControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FormMethod?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.IControlAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Image?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.IObjectListFieldCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.IPageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ItemPager?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ITemplateable?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Label?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Link?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.List?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListCommandEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListCommandEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListDataBindEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListDataBindEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListDecoration?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListSelectType?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralLink?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralText?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralTextContainerControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralTextControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LoadItemsEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LoadItemsEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControl?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControlsSection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControlsSectionHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileListItem?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileListItemCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileListItemType?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobilePage?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileTypeNameConverter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileUserControl?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectList?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommand?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListField?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListFieldCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListItem?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListItemCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListTitleAttribute?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListViewMode?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PagedControl?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PagerStyle?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Panel?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PanelControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PersistNameAttribute?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PhoneCall?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.RangeValidator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.RegularExpressionValidator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.RequiredFieldValidator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.SelectionList?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Style?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.StyleSheet?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.StyleSheetControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TemplateContainer?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextBox?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextBoxControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextControl?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextView?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextViewElement?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ValidationSummary?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Wrapping?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCalendarAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCommandAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlFormAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlImageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlLinkAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlMobileTextWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPhoneCallAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlSelectionListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlTextBoxAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ControlAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCalendarAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCommandAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlControlAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlFormAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlImageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLabelAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLinkAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLiteralTextAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlMobileTextWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlObjectListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPanelAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPhoneCallAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlSelectionListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextBoxAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextViewAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidationSummaryAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidatorAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.MobileTextWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.MultiPartWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlMobileTextWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlPageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCalendarAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCommandAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlControlAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlFormAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlImageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLabelAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLinkAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLiteralTextAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlMobileTextWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlObjectListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPanelAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPhoneCallAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPostFieldType?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlSelectionListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextBoxAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextViewAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidationSummaryAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidatorAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.Doctype?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.StyleSheetLocation?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCalendarAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCommandAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlControlAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCssHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlFormAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlImageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLabelAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLinkAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLiteralTextAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlMobileTextWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlObjectListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPanelAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPhoneCallAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlSelectionListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextBoxAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextViewAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidationSummaryAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidatorAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll bylo zastaralé a nemělo by se používat. Informace o vývoji mobilních aplikací ASP.NET naleznete v [tématu ASP.NET for Mobiles](/aspnet/mobile/overview).|

[Zpět na začátek](#introduction)

<a name="workflow_activities"></a>

### <a name="assembly-systemworkflowactivitiesdll"></a>Sestava: System.Workflow.Activities.dll

|Typ|Zpráva|
|----------|-------------|
|Všechny typy <xref:System.Workflow.Activities?displayProperty=nameWithType> v oboru názvů|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|<xref:System.Workflow.Activities.Configuration.ActiveDirectoryRoleFactoryConfiguration?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|<xref:System.Workflow.Activities.Rules.RuleActionTrackingEvent?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|<xref:System.Workflow.Activities.Rules.RuleConditionReference?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|<xref:System.Workflow.Activities.Rules.RuleSetReference?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|

[Zpět na začátek](#introduction)

<a name="workflow_componentmodel"></a>

### <a name="assembly-systemworkflowcomponentmodeldll"></a>Sestava: System.Workflow.ComponentModel.dll

|Typ|Zpráva|
|----------|-------------|
|Všechny typy <xref:System.Workflow.ComponentModel> v oboru <xref:System.Workflow.ComponentModel.GetValueOverride?displayProperty=nameWithType> názvů s výjimkou a<xref:System.Workflow.ComponentModel.SetValueOverride?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|Všechny typy <xref:System.Workflow.ComponentModel.Compiler> v oboru <xref:System.Workflow.ComponentModel.Compiler.ValidationError?displayProperty=nameWithType> názvů s výjimkou a<xref:System.Workflow.ComponentModel.Compiler.ValidationErrorCollection?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|Všechny typy <xref:System.Workflow.ComponentModel.Design> v oboru názvů s výjimkou<xref:System.Workflow.ComponentModel.Design.ConnectorEventHandler>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializationManager?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializer?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityMarkupSerializer?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivitySurrogateSelector?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityTypeCodeDomSerializer?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.CompositeActivityMarkupSerializer?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|<xref:System.Workflow.ComponentModel.Serialization.DependencyObjectCodeDomSerializer?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|

[Zpět na začátek](#introduction)

<a name="workflow_runtime"></a>

### <a name="assembly-systemworkflowruntimedll"></a>Sestava: System.Workflow.Runtime.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Activities.Statements.Interop?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br />Typy Workflow Foundation 3.0 jsou zastaralé. Místo toho použijte typy pracovního <xref:System.Activities>postupu 4.0 z aplikace . \*.|
|<xref:System.Activities.Tracking.InteropTrackingRecord?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br />Typy Workflow Foundation 3.0 jsou zastaralé. Místo toho použijte typy pracovního <xref:System.Activities>postupu 4.0 z aplikace . \*.|
|Všechny typy <xref:System.Workflow.Runtime> v oboru názvů|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|Všechny typy <xref:System.Workflow.Runtime.Configuration> v oboru názvů|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|Všechny typy <xref:System.Workflow.Runtime.DebugEngine> v oboru názvů s výjimkou<xref:System.Workflow.Runtime.DebugEngine.DebugEngineCallback>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|Všechny typy <xref:System.Workflow.Runtime.Hosting> v oboru názvů s výjimkou<xref:System.Workflow.Runtime.Hosting.WorkflowCommitWorkBatchService.CommitWorkBatchCallback>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|
|Všechny typy <xref:System.Workflow.Runtime.Tracking> v oboru názvů|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> The System.Workflow. \* typy jsou zastaralé. Místo toho použijte nové <xref:System.Activities>typy z . \*.|

[Zpět na začátek](#introduction)

<a name="workflowservices"></a>

### <a name="assembly-systemworkflowservicesdll"></a>Sestava: System.WorkflowServices.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.ServiceModel.WorkflowServiceHost?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Activation.WorkflowServiceHostFactory?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Activities.Description.WorkflowRuntimeEndpoint?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Configuration.ExtendedWorkflowRuntimeServiceElementCollection?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Configuration.PersistenceProviderElement?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Configuration.WorkflowRuntimeElement?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Description.DurableOperationAttribute?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Description.DurableServiceAttribute?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Description.PersistenceProviderBehavior?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Description.UnknownExceptionAction?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Description.WorkflowRuntimeBehavior?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Dispatcher.DurableOperationContext?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Persistence.InstanceLockException?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Persistence.InstanceNotFoundException?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Persistence.LockingPersistenceProvider?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Persistence.PersistenceException?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Persistence.PersistenceProvider?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Persistence.PersistenceProviderFactory?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|Všechny typy <xref:System.Workflow.Activities?displayProperty=nameWithType> v oboru názvů|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|
|<xref:System.Workflow.Runtime.Hosting.ChannelManagerService?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Typy WF 3 jsou zastaralé. Místo toho použijte nové typy <xref:System.Activities>WF 4 od . \*.|

[Zpět na začátek](#introduction)

<a name="xaml"></a>

### <a name="assembly-systemxamldll"></a>Sestava: System.Xaml.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute?displayProperty=nameWithType>|To není používán analyzátorem XAML. Prosím, <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=nameWithType>podívejte se na .|

[Zpět na začátek](#introduction)

<a name="xml"></a>

### <a name="assembly-systemxmldll"></a>Sestavení: System.Xml.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Xml.IApplicationResourceStreamResolver?displayProperty=nameWithType>|První zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu generuje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Xml.Schema.XmlSchemaCollection?displayProperty=nameWithType>|Slouží <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> k kompilaci a ověřování schématu.|
|<xref:System.Xml.XmlValidatingReader?displayProperty=nameWithType>|Použijte <xref:System.Xml.XmlReader?displayProperty=nameWithType> vytvořenou <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> metodou pomocí <xref:System.Xml.XmlReaderSettings?displayProperty=nameWithType> příslušného.|
|<xref:System.Xml.XmlXapResolver?displayProperty=nameWithType>|Použití tohoto typu generuje chybu kompilátoru. Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>|Tato třída byla zastaralá. Použijte <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType> místo toho.|

[Zpět na začátek](#introduction)

<a name="WindowsBase"></a>

### <a name="assembly-windowsbasedll"></a>Sestavení: WindowsBase.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType>|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType>byla zastaralá. Toto rozhraní se již nepoužívá.|

[Zpět na začátek](#introduction)

<a name="obsolete_types_in_microsoft_assemblies"></a>

## <a name="obsolete-types-in-microsoft-assemblies"></a>Zastaralé typy v sestaveních společnosti Microsoft

V následujících částech jsou uvedeny zastaralé typy v sestaveních společnosti Microsoft. Tato sestavení jsou speciální sestavení, jako jsou sestavení, která cílí na jednotlivé jazyky (například Microsoft.JScript.dll nebo Microsoft.VisualC.dll).

<a name="IEHost"></a>

### <a name="assembly-iehostdll-and-ieexecexe"></a>Sestavení: IEHost.dll a IEExec.exe

Sestavení IEHost.dll a IEExec.exe byla odebrána z rozhraní .NET Framework. Všechny jejich typy a jejich členy jsou zastaralé a nejsou podporovány jako rozhraní .NET Framework 4. Tato sestavení byla použita k hostování ovládacích prvků windows forms a ke spuštění spustitelných souborů v aplikaci Internet Explorer. Mezi doporučené alternativy patří ClickOnce, XAML aplikace prohlížeče (XBAP) a Microsoft Silverlight.

[Zpět na začátek](#introduction)

<a name="Engine"></a>

### <a name="assembly-microsoftbuildenginedll"></a>Sestavení: Microsoft.Build.Engine.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=nameWithType>|Tato třída byla zastaralá. Místo <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> toho použijte sestavení *Microsoft.Build.*|
|<xref:Microsoft.Build.BuildEngine.Project?displayProperty=nameWithType>|Tato třída byla zastaralá. Místo <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> toho použijte sestavení *Microsoft.Build.*|

[Zpět na začátek](#introduction)

<a name="jscript"></a>

### <a name="assembly-microsoftjscriptdll"></a>Sestavení: Microsoft.JScript.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:Microsoft.JScript.Vsa.BaseVsaEngine?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.BaseVsaSite?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.BaseVsaStartup?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.IJSVsaCodeItem?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.IJSVsaEngine?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.IJSVsaError?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.IJSVsaGlobalItem?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItem?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItems?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.IJSVsaPersistSite?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.IJSVsaReferenceItem?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.IJSVsaSite?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.JSVsaError?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.JSVsaException?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemFlag?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemType?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.ResInfo?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|
|<xref:Microsoft.JScript.Vsa.VsaEngine?displayProperty=nameWithType>|Tento typ byl v sadě Visual Studio 2005 zastaral. neexistuje žádná náhrada za tuto funkci. Další nápovědu naleznete v <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci.|

[Zpět na začátek](#introduction)

<a name="VBCompat"></a>

### <a name="assembly-microsoftvisualbasiccompatibilitydll"></a>Sestavení: Microsoft.VisualBasic.Compatibility.dll

Informace o migraci z jazyka Visual Basic 6 naleznete v [centru zdrojů jazyka Visual Basic 6.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-basic-6/visual-basic-6.0-documentation).

|Typ|Zpráva|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseControlArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseOcxArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ButtonArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckBoxArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckedListBoxArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ColorDialogArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ComboBoxArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBox?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBoxArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBox?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBoxArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBox?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBoxArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FixedLengthString?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FontDialogArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FormShowConstants?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.GroupBoxArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.HScrollBarArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ImageListArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LabelArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxItem?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListViewArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LoadResConstants?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MaskedTextBoxArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MenuItemArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MouseButtonConstants?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.OpenFileDialogArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PanelArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PictureBoxArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PrintDialogArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ProgressBarArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RadioButtonArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RichTextBoxArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SaveFileDialogArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ScaleMode?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ShiftConstants?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusBarArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusStripArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.Support?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TabControlArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TextBoxArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TimerArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolBarArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripMenuItemArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TreeViewArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.VScrollBarArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebBrowserArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClass?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassContainingClassNotOptional?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassCouldNotFindEvent?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemCannotBeCurrentWebItem?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemRespondNotFound?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassUserWebClassNameNotOptional?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebClassFileNameNotOptional?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebItemNotValid?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItem?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemAssociatedWebClassNotOptional?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemClosingTagNotFound?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadEmbeddedResource?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadTemplateFile?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNameNotOptional?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNoTemplateSpecified?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemTooManyNestedTags?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemUnexpectedErrorReadingTemplateFile?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ZOrderConstants?displayProperty=nameWithType>|Tento člen je zastaralý.|

[Zpět na začátek](#introduction)

<a name="VBCompatData"></a>

### <a name="assembly-microsoftvisualbasiccompatibilitydatadll"></a>Sestavení: Microsoft.VisualBasic.Compatibility.Data.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.BOFActionEnum?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EndOfRecordsetDelegate?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EOFActionEnum?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.ErrorDelegate?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchCompleteDelegate?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchProgressDelegate?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FieldChangeCompleteDelegate?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.MoveCompleteDelegate?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.OrientationEnum?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordChangeCompleteDelegate?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordsetChangeCompleteDelegate?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeFieldDelegate?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordDelegate?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordsetDelegate?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillMoveDelegate?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODCArray?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseDataEnvironment?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BindingCollectionEnumerator?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CONNECTDATA?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBBINDING?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBCOLUMNINFO?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBID?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBinding?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBindingCollection?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBKINDENUM?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBPROPIDSET?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IAccessor?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IChapteredRowset?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IColumnsInfo?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPoint?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPointContainer?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormat?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormatDisp?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnectionPoints?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnections?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPosition?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPositionChange?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowset?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetChange?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetIdentity?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetInfo?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetNotify?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBinding?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBindingCollection?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SRDescriptionAttribute?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UGUID?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UNAME?displayProperty=nameWithType>|Tento člen je zastaralý.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UpdateMode?displayProperty=nameWithType>|Tento člen je zastaralý.|

[Zpět na začátek](#introduction)

<a name="visualc"></a>

### <a name="assembly-microsoftvisualcdll"></a>Sestavení: Microsoft.VisualC.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:Microsoft.VisualC.DebugInfoInPDBAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll je zastaralé sestavení a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.DecoratedNameAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll je zastaralé sestavení a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.IsConstModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je zastaralé sestavení a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.IsCXXReferenceModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je zastaralé sestavení a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.IsLongModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je zastaralé sestavení a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.IsSignedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je zastaralé sestavení a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.IsVolatileModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je zastaralé sestavení a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.MiscellaneousBitsAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll je zastaralé sestavení a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.NeedsCopyConstructorModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je zastaralé sestavení a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.NoSignSpecifiedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je zastaralé sestavení a existuje pouze pro zpětnou kompatibilitu.|

## <a name="see-also"></a>Viz také

- [Zastaralé položky v knihovně tříd](whats-obsolete.md)
- [Zastaralé členy](obsolete-members.md)
