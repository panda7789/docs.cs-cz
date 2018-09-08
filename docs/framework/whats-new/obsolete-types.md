---
title: Zastaralé typy v rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, obsolete types
- types, obsolete in .NET Framework 4.5
- obsolete types [.NET Framework]
ms.assetid: e636d024-0fac-45eb-b721-25a8c0ceca8f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab4d3bf7db928f926b802c08ee5e61edf86055b6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44173204"
---
# <a name="obsolete-types-in-the-net-framework"></a>Zastaralé typy v rozhraní .NET Framework
<a name="introduction"></a> V tabulkách v tomto článku jsou uvedeny typy, které jsou zastaralé v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]uspořádaných podle sestavení. Pokud chcete zobrazit seznam zastaralých typů a doporučené alternativy v každé sestavení pomocí následujících odkazů. Protože tyto typy jsou zastaralé, jsou zastaralé také jejich členy. Seznam dalších zastaralé členy v knihovně tříd rozhraní .NET Framework najdete v tématu [zastaralé členy](../../../docs/framework/whats-new/obsolete-members.md).

-   [Zastaralé typy v systému sestavení](#obsolete_types_in_system_assemblies)

    -   [mscorlib.dll](#mscorlib)

    -   [System.Core.dll](#Core)

    -   [System.Data.dll](#data)

    -   [System.Data.OracleClient.dll](#oracleclient)

    -   [System.Design.dll](#design)

    -   [System.dll](#system)

    -   [System.EnterpriseServices.dll](#enterpriseservices)

    -   [System.Net.dll](#net)

    -   [System.ServiceModel.dll](#servicemodel)

    -   [System.Web.dll](#web)

    -   [System.Web.Mobile.dll](#mobile)

    -   [System.Workflow.Activities.dll](#workflow_activities)

    -   [System.Workflow.ComponentModel.dll](#workflow_componentmodel)

    -   [System.Workflow.Runtime.dll](#workflow_runtime)

    -   [System.WorkflowServices.dll](#workflowservices)

    -   [System.Xaml.dll](#xaml)

    -   [System.Xml.dll](#xml)

    -   [WindowsBase.dll](#WindowsBase)

-   [Zastaralé typy v sestavení společnosti Microsoft](#obsolete_types_in_microsoft_assemblies)

    -   [IEHost.dll a IEExec.exe](#IEHost)

    -   [Microsoft.Build.Engine.dll](#Engine)

    -   [Microsoft.JScript.dll](#jscript)

    -   [Microsoft.VisualBasic.Compatibility.dll](#VBCompat)

    -   [Microsoft.VisualBasic.Compatibility.Data.dll](#VBCompatData)

    -   [Microsoft.VisualC.dll](#visualc)

<a name="obsolete_types_in_system_assemblies"></a>
## <a name="obsolete-types-in-system-assemblies"></a>Zastaralé typy v systému sestavení
 V následujících tabulkách jsou uvedeny typy, které byly prohlášeny za zastaralé v systému sestavení. Tato sestavení se používají pro obecné\-účely vývoje aplikací, které cílí na .NET Framework.

<a name="mscorlib"></a>
### <a name="assembly-mscorlibdll"></a>Sestavení: mscorlib.dll.

|Typ|Zpráva|
|----------|-------------|
|<xref:System.ExecutionEngineException?displayProperty=nameWithType>|Tento typ dříve uvedené neurčené závažná chyba v modulu runtime. Modul runtime již nadále nevyvolává tuto výjimku, takže tento typ je zastaralé.|
|<xref:System.Collections.CaseInsensitiveHashCodeProvider?displayProperty=nameWithType>|Použijte prosím <xref:System.StringComparer?displayProperty=nameWithType> místo.|
|<xref:System.Collections.IHashCodeProvider?displayProperty=nameWithType>|Použijte prosím <xref:System.Collections.IEqualityComparer?displayProperty=nameWithType> místo.|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|<xref:System.Configuration.Assemblies.AssemblyHash> Třída je zastaralá.|
|<xref:System.Diagnostics.Contracts.Internal.ContractHelper?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5. Použití <xref:System.Runtime.CompilerServices.ContractHelper?displayProperty=nameWithType> třídy v oboru názvů System.Runtime.CompilerServices místo.|
|<xref:System.Reflection.Emit.UnmanagedMarshal?displayProperty=nameWithType>|Alternativní rozhraní API je k dispozici: generování <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> vlastního atributu místo.|
|<xref:System.Runtime.InteropServices.BIND_OPTS?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.BIND_OPTS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.BINDPTR?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.BINDPTR?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.CALLCONV?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.CALLCONV?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.CONNECTDATA?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.CONNECTDATA?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.DESCKIND?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.DESCKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.DISPPARAMS?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.DISPPARAMS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.ELEMDESC?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.ELEMDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.EXCEPINFO?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.EXCEPINFO?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FILETIME?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.FILETIME?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FUNCDESC?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.FUNCDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FUNCFLAGS?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.FUNCFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.FUNCKIND?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.FUNCKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType>|Tento atribut je zastaralá a bude v budoucí verzi odebrána.|
|<xref:System.Runtime.InteropServices.IDispatchImplType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType> Je zastaralý.|
|<xref:System.Runtime.InteropServices.IDLDESC?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IDLDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.IDLFLAG?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IDLFLAG?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.IMPLTYPEFLAGS?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IMPLTYPEFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.INVOKEKIND?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.INVOKEKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.LIBFLAGS?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.LIBFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.PARAMDESC?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.PARAMDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.PARAMFLAG?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.PARAMFLAG?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.SetWin32ContextInIDispatchAttribute?displayProperty=nameWithType>|Tento atribut je zastaralá. Aplikační domény už nebude respektovat aktivační kontext hranice ve volání rozhraní IDispatch.|
|<xref:System.Runtime.InteropServices.STATSTG?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.STATSTG?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.SYSKIND?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.SYSKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEATTR?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.TYPEATTR?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEDESC?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.TYPEDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEFLAGS?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.TYPEFLAGS?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPEKIND?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.TYPEKIND?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.TYPELIBATTR?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.TYPELIBATTR?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIBindCtx?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IBindCtx?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPoint?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPointContainer?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnectionPoints?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IEnumConnectionPoints?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnections?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IEnumConnections?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumMoniker?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IEnumMoniker?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumString?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IEnumString?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIEnumVARIANT?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIMoniker?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IMoniker?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIPersistFile?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IPersistFile?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIRunningObjectTable?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IRunningObjectTable?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMIStream?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMITypeComp?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.ITypeComp?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMITypeInfo?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.UCOMITypeLib?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.ITypeLib?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.VARDESC?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.VARDESC?displayProperty=nameWithType>.|
|<xref:System.Runtime.InteropServices.VARFLAGS?displayProperty=nameWithType>|Místo nich se používá <xref:System.Runtime.InteropServices.ComTypes.VARFLAGS?displayProperty=nameWithType>.|
|<xref:System.Security.SecurityCriticalScope?displayProperty=nameWithType>|<xref:System.Security.SecurityCriticalScope> slouží pouze pro kompatibilitu transparentnosti rozhraní .NET 2.0.|
|<xref:System.Security.SecurityTreatAsSafeAttribute?displayProperty=nameWithType>|<xref:System.Security.SecurityTreatAsSafeAttribute> slouží pouze pro kompatibilitu transparentnosti rozhraní .NET 2.0. Použijte prosím <xref:System.Security.SecuritySafeCriticalAttribute?displayProperty=nameWithType> místo.|
|<xref:System.Security.Policy.FirstMatchCodeGroup?displayProperty=nameWithType>|Tento typ je zastaralá a v příští verzi rozhraní .NET Framework se odebere.|
|<xref:System.Security.Policy.PermissionRequestEvidence?displayProperty=nameWithType>|Deklarativní zabezpečení na úrovni sestavení je zastaralá a je už nebudou vynucené modulem CLR ve výchozím nastavení.|
|<xref:System.Security.Policy.UnionCodeGroup?displayProperty=nameWithType>|Tento typ je zastaralá a v příští verzi rozhraní .NET Framework se odebere.|

 [Zpět na začátek](#introduction)

<a name="Core"></a>
### <a name="assembly-systemcoredll"></a>Assembly: System.Core.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Runtime.CompilerServices.ExecutionScope?displayProperty=nameWithType>|Použití tohoto typu vygeneruje chybu kompilátoru.<br /><br /> Nepoužívejte tohoto typu.|

 [Zpět na začátek](#introduction)

<a name="data"></a>
### <a name="assembly-systemdatadll"></a>Assembly: System.Data.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=nameWithType>|<xref:System.Data.DataSysDescriptionAttribute> se už nepoužívá.|
|<xref:System.Data.PropertyAttributes?displayProperty=nameWithType>|<xref:System.Data.PropertyAttributes> se už nepoužívá.|
|<xref:System.Data.TypedDataSetGenerator?displayProperty=nameWithType>|<xref:System.Data.TypedDataSetGenerator> v budoucí verzi se odebere třídy. Použijte prosím <xref:System.Data.Design.TypedDataSetGenerator?displayProperty=nameWithType> v System.Design.dll.|
|<xref:System.Xml.XmlDataDocument?displayProperty=nameWithType>|<xref:System.Xml.XmlDataDocument> v budoucí verzi se odebere třídy.|

 [Zpět na začátek](#introduction)

<a name="oracleclient"></a>
### <a name="assembly-systemdataoracleclientdll"></a>Assembly: System.Data.OracleClient.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Data.OracleClient.OracleClientFactory?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleClientFactory> se už nepoužívá.|
|<xref:System.Data.OracleClient.OracleCommand?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommand> se už nepoužívá.|
|<xref:System.Data.OracleClient.OracleCommandBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommandBuilder> se už nepoužívá.|
|<xref:System.Data.OracleClient.OracleConnection?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnection> se už nepoužívá.|
|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder> se už nepoužívá.|
|<xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleDataAdapter> se už nepoužívá.|
|<xref:System.Data.OracleClient.OraclePermission?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermission> se už nepoužívá.|
|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType> se už nepoužívá.|

 [Zpět na začátek](#introduction)

<a name="design"></a>
### <a name="assembly-systemdesigndll"></a>Sestavení: System.Design.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.ComponentModel.Design.LocalizationExtenderProvider?displayProperty=nameWithType>|Tato třída je zastaralá. Místo nich se používá <xref:System.ComponentModel.Design.Serialization.CodeDomLocalizationProvider?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.DataBindingCollectionConverter?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože úpravy vazeb dat se spustí prostřednictvím <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> místo mřížku vlastností.|
|<xref:System.Web.UI.Design.DataBindingCollectionEditor?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože úpravy vazeb dat se spustí prostřednictvím <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> místo mřížku vlastností.|
|<xref:System.Web.UI.Design.IControlDesignerBehavior?displayProperty=nameWithType>|Doporučenou alternativou je <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> a <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IHtmlControlDesignerBehavior?displayProperty=nameWithType>|Doporučenou alternativou je <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> a <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ITemplateEditingFrame?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože úpravy šablony je zpracována v <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. K podpoře úprav šablony, zpřístupnit data šablony v <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> vlastnosti a volání <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IWebFormReferenceManager?displayProperty=nameWithType>|Doporučenou alternativou je <xref:System.Web.UI.Design.WebFormsReferenceManager?displayProperty=nameWithType>. <xref:System.Web.UI.Design.WebFormsReferenceManager> Obsahuje další funkce a umožňuje pro další rozšíření. Chcete-li získat <xref:System.Web.UI.Design.WebFormsReferenceManager>, použijte `RootDesigner.ReferenceManager` vlastnost z vaší <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IWebFormsDocumentService?displayProperty=nameWithType>|Doporučenou alternativou je <xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=nameWithType>. <xref:System.Web.UI.Design.WebFormsRootDesigner> Obsahuje další funkce a umožňuje pro další rozšíření. Chcete-li získat <xref:System.Web.UI.Design.WebFormsRootDesigner>, použijte <xref:System.Web.UI.Design.ControlDesigner.RootDesigner%2A> vlastnost z vaší <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ITemplateEditingService?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože úpravy šablony je zpracována v <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. K podpoře úprav šablony, zpřístupnit data šablony v <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> vlastnosti a volání <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ReadWriteControlDesigner?displayProperty=nameWithType>|Doporučenou alternativou je <xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=nameWithType> protože používá <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> pro úpravy obsahu. Oblasti návrháře umožňuje lepší kontrolu obsahu, který právě upravujete.|
|<xref:System.Web.UI.Design.TemplateEditingService?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože úpravy šablony je zpracována v <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. K podpoře úprav šablony, zpřístupnit data šablony v <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> vlastnosti a volání <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.TemplateEditingVerb?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože úpravy šablony je zpracována v <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. K podpoře úprav šablony, zpřístupnit data šablony v <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> vlastnosti a volání <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.WebControls.CalendarAutoFormatDialog?displayProperty=nameWithType>|Použití tohoto typu se nedoporučuje, protože hostitel návrháře je spouštěn AutoFormat – dialogové okno. Seznam dostupných automatických formátů je vystaven na <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> v <xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=nameWithType> vlastnost.|
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=nameWithType>|Doporučenou alternativou je <xref:System.Web.UI.Design.WebControls.PanelContainerDesigner?displayProperty=nameWithType> protože používá <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> pro úpravy obsahu. Oblasti návrháře umožňuje lepší kontrolu obsahu, který právě upravujete.|

 [Zpět na začátek](#introduction)

<a name="system"></a>
### <a name="assembly-systemdll"></a>Sestavení: System.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.ComponentModel.IComNativeDescriptorHandler?displayProperty=nameWithType>|Toto rozhraní se už nepoužívá. Přidat <xref:System.ComponentModel.TypeDescriptionProvider?displayProperty=nameWithType> ke zpracování typu <xref:System.ComponentModel.TypeDescriptor.ComObjectType%2A?displayProperty=nameWithType> místo.|
|<xref:System.ComponentModel.RecommendedAsConfigurableAttribute?displayProperty=nameWithType>|Použití <xref:System.ComponentModel.SettingsBindableAttribute?displayProperty=nameWithType> místo pro práci s novým modelem nastavení.|
|<xref:System.ComponentModel.Design.Serialization.RootDesignerSerializerAttribute?displayProperty=nameWithType>|Tento atribut je zastaralá. Místo nich se používá <xref:System.ComponentModel.Design.Serialization.DesignerSerializerAttribute?displayProperty=nameWithType>. Například pokud chcete zadat Návrhář kořenových aktivit pro CodeDom, použít `DesignerSerializerAttribute\(...,typeof\(TypeCodeDomSerializer\)\)`.|
|<xref:System.Diagnostics.DiagnosticsConfigurationHandler?displayProperty=nameWithType>|Tato třída je zastaralá.|
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=nameWithType>|Tato třída je zastaralá. Použití čítačů výkonu prostřednictvím <xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType> namísto třídy.|
|<xref:System.Net.GlobalProxySelection?displayProperty=nameWithType>|Tato třída je zastaralá. Použijte prosím <xref:System.Net.WebRequest.DefaultWebProxy%2A?displayProperty=nameWithType> místo toho k přístupu a nastavte globální výchozí proxy server. Namísto použití 'null' <xref:System.Net.GlobalProxySelection.GetEmptyWebProxy%2A?displayProperty=nameWithType>.|
|<xref:System.Net.Sockets.SocketClientAccessPolicyProtocol?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu vygeneruje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|

 [Zpět na začátek](#introduction)

<a name="enterpriseservices"></a>
### <a name="assembly-systementerpriseservicesdll"></a>Assembly: System.EnterpriseServices.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.EnterpriseServices.RegistrationHelperTx?displayProperty=nameWithType>|<xref:System.EnterpriseServices.RegistrationHelperTx> Třída je zastaralá.|

 [Zpět na začátek](#introduction)

<a name="net"></a>
### <a name="assembly-systemnetdll"></a>Assembly: System.Net.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Net.INetworkProgress?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu vygeneruje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.IUnsafeWebRequestCreate?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu vygeneruje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.NetworkProgressChangedEventArgs?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu vygeneruje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.UiSynchronizationContext?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu vygeneruje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.Sockets.HttpPolicyDownloaderProtocol?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu vygeneruje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.Sockets.SecurityCriticalAction?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu vygeneruje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.Sockets.SocketPolicy?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu vygeneruje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.Sockets.UdpAnySourceMulticastClient?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu vygeneruje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Net.Sockets.UdpSingleSourceMulticastClient?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu vygeneruje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|

 [Zpět na začátek](#introduction)

<a name="servicemodel"></a>
### <a name="assembly-systemservicemodeldll"></a>Assembly: System.ServiceModel.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.ServiceModel.NetPeerTcpBinding?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkci peer channel je zastaralá a v budoucnu se odebere.|
|<xref:System.ServiceModel.Channels.HttpCookieContainerBindingElement?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Tento typ je zastaralé. Povolení protokolu Http <xref:System.Net.CookieContainer>, použijte `AllowCookies` vlastnost pro vazbu protokolu Http nebo na <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.|
|<xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkci peer channel je zastaralá a v budoucnu se odebere.|
|<xref:System.ServiceModel.Channels.PeerTransportBindingElement?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkci peer channel je zastaralá a v budoucnu se odebere.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingCollectionElement?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkci peer channel je zastaralá a v budoucnu se odebere.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkci peer channel je zastaralá a v budoucnu se odebere.|
|<xref:System.ServiceModel.Configuration.PeerTransportElement?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkci peer channel je zastaralá a v budoucnu se odebere.|
|<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Funkci peer channel je zastaralá a v budoucnu se odebere.|

 [Zpět na začátek](#introduction)

<a name="web"></a>
### <a name="assembly-systemwebdll"></a>Assembly: System.Web.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Web.Configuration.PassportAuthentication?displayProperty=nameWithType>|Tento typ je zastaralé. Produkt ověřování služby Passport se už nepodporuje a bylo nahrazeno [Account Microsoft](https://go.microsoft.com/fwlink/?LinkId=733413)|
|<xref:System.Web.Mail.MailAttachment?displayProperty=nameWithType>|Doporučenou alternativou je <xref:System.Net.Mail.Attachment?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailEncoding?displayProperty=nameWithType>|Doporučenou alternativou je <xref:System.Net.Mime.TransferEncoding?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailFormat?displayProperty=nameWithType>|Doporučenou alternativou je <xref:System.Net.Mail.MailMessage.IsBodyHtml%2A?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>|Doporučenou alternativou je <xref:System.Net.Mail.MailMessage?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailPriority?displayProperty=nameWithType>|Doporučenou alternativou je <xref:System.Net.Mail.MailPriority?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.SmtpMail?displayProperty=nameWithType>|Doporučenou alternativou je <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>.|
|<xref:System.Web.Security.PassportAuthenticationEventArgs?displayProperty=nameWithType>|Tento typ je zastaralé. Produkt ověřování služby Passport se už nepodporuje a bylo nahrazeno [Account Microsoft](https://go.microsoft.com/fwlink/?LinkId=733413)|
|<xref:System.Web.Security.PassportAuthenticationEventHandler?displayProperty=nameWithType>|Tento typ je zastaralé. Produkt ověřování služby Passport se už nepodporuje a bylo nahrazeno [Account Microsoft](https://go.microsoft.com/fwlink/?LinkId=733413)|
|<xref:System.Web.Security.PassportAuthenticationModule?displayProperty=nameWithType>|Tento typ je zastaralé. Produkt ověřování služby Passport se už nepodporuje a bylo nahrazeno [Account Microsoft](https://go.microsoft.com/fwlink/?LinkId=733413)|
|<xref:System.Web.Security.PassportIdentity?displayProperty=nameWithType>|Tento typ je zastaralé. Produkt ověřování služby Passport se už nepodporuje a bylo nahrazeno [Account Microsoft](https://go.microsoft.com/fwlink/?LinkId=733413)|
|<xref:System.Web.Security.PassportPrincipal?displayProperty=nameWithType>|Tento typ je zastaralé. Produkt ověřování služby Passport se už nepodporuje a bylo nahrazeno [Account Microsoft](https://go.microsoft.com/fwlink/?LinkId=733413)|
|<xref:System.Web.UI.ObjectConverter?displayProperty=nameWithType>|Doporučenou alternativou je <xref:System.Convert?displayProperty=nameWithType> a <xref:System.String.Format%2A?displayProperty=nameWithType>.|

 [Zpět na začátek](#introduction)

<a name="mobile"></a>
### <a name="assembly-systemwebmobiledll"></a>Assembly: System.Web.Mobile.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Web.Mobile.CookielessData?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.DeviceFilterElement?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.DeviceFilterElementCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.DeviceFiltersSection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.ErrorHandlerModule?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.MobileCapabilities?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.MobileDeviceCapabilitiesSectionHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.MobileErrorInfo?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.Mobile.MobileFormsAuthentication?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.Design.MobileControls.IMobileDesigner?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.Design.MobileControls.IMobileWebFormServices?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.Design.MobileControls.MobileResource?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataFieldConverter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataMemberConverter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.AdRotator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Alignment?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ArrayListCollectionBase?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.BaseValidator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.BooleanOption?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Calendar?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Command?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.CommandFormat?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.CompareValidator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Constants?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ControlElement?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ControlElementCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ControlPager?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.CustomValidator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DesignerAdapterAttribute?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceElement?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceElementCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceOverridableAttribute?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecific?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoice?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateContainer?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ErrorFormatterPage?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.FontInfo?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.FontSize?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Form?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.FormControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.FormMethod?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.IControlAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Image?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.IObjectListFieldCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.IPageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ItemPager?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ITemplateable?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Label?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Link?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.List?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListCommandEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListCommandEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListDataBindEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListDataBindEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListDecoration?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ListSelectType?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.LiteralLink?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.LiteralText?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.LiteralTextContainerControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.LiteralTextControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.LoadItemsEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.LoadItemsEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileControl?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileControlsSection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileControlsSectionHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileListItem?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileListItemCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileListItemType?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobilePage?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileTypeNameConverter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.MobileUserControl?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectList?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListCommand?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListField?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListFieldCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListItem?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListItemCollection?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventArgs?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListTitleAttribute?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ObjectListViewMode?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.PagedControl?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.PagerStyle?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Panel?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.PanelControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.PersistNameAttribute?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.PhoneCall?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.RangeValidator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.RegularExpressionValidator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.RequiredFieldValidator?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.SelectionList?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Style?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.StyleSheet?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.StyleSheetControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.TemplateContainer?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.TextBox?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.TextBoxControlBuilder?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.TextControl?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.TextView?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.TextViewElement?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.ValidationSummary?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Wrapping?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCalendarAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCommandAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlFormAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlImageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlLinkAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlMobileTextWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPhoneCallAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlSelectionListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlTextBoxAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.ControlAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCalendarAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCommandAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlControlAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlFormAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlImageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLabelAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLinkAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLiteralTextAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlMobileTextWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlObjectListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPanelAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPhoneCallAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlSelectionListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextBoxAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextViewAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidationSummaryAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidatorAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.MobileTextWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.MultiPartWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlMobileTextWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlPageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCalendarAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCommandAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlControlAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlFormAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlImageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLabelAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLinkAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLiteralTextAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlMobileTextWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlObjectListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPanelAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPhoneCallAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPostFieldType?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlSelectionListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextBoxAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextViewAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidationSummaryAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidatorAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.Doctype?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.StyleSheetLocation?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCalendarAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCommandAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlControlAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCssHandler?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlFormAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlImageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLabelAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLinkAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLiteralTextAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlMobileTextWriter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlObjectListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPageAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPanelAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPhoneCallAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlSelectionListAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextBoxAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextViewAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidationSummaryAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidatorAdapter?displayProperty=nameWithType>|Sestavení System.Web.Mobile.dll se už nepoužívá a by měl být už nebude používat. Informace o tom, jak vývoj mobilních aplikací ASP.NET, naleznete v tématu [ASP.NET pro mobilní telefony](https://go.microsoft.com/fwlink/?LinkId=157231).|

 [Zpět na začátek](#introduction)

<a name="workflow_activities"></a>
### <a name="assembly-systemworkflowactivitiesdll"></a>Sestavení: System.Workflow.Activities.dll

|Typ|Zpráva|
|----------|-------------|
|Všechny typy v <xref:System.Workflow.Activities?displayProperty=nameWithType> obor názvů|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|<xref:System.Workflow.Activities.Configuration.ActiveDirectoryRoleFactoryConfiguration?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|<xref:System.Workflow.Activities.Rules.RuleActionTrackingEvent?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|<xref:System.Workflow.Activities.Rules.RuleConditionReference?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|<xref:System.Workflow.Activities.Rules.RuleSetReference?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|

 [Zpět na začátek](#introduction)

<a name="workflow_componentmodel"></a>
### <a name="assembly-systemworkflowcomponentmodeldll"></a>Assembly: System.Workflow.ComponentModel.dll

|Typ|Zpráva|
|----------|-------------|
|Všechny typy v <xref:System.Workflow.ComponentModel> oboru názvů s výjimkou <xref:System.Workflow.ComponentModel.GetValueOverride?displayProperty=nameWithType> a <xref:System.Workflow.ComponentModel.SetValueOverride?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|Všechny typy v <xref:System.Workflow.ComponentModel.Compiler> oboru názvů s výjimkou <xref:System.Workflow.ComponentModel.Compiler.ValidationError?displayProperty=nameWithType> a <xref:System.Workflow.ComponentModel.Compiler.ValidationErrorCollection?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|Všechny typy v <xref:System.Workflow.ComponentModel.Design> oboru názvů s výjimkou <xref:System.Workflow.ComponentModel.Design.ConnectorEventHandler>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializationManager?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializer?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityMarkupSerializer?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivitySurrogateSelector?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityTypeCodeDomSerializer?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.CompositeActivityMarkupSerializer?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|<xref:System.Workflow.ComponentModel.Serialization.DependencyObjectCodeDomSerializer?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|

 [Zpět na začátek](#introduction)

<a name="workflow_runtime"></a>
### <a name="assembly-systemworkflowruntimedll"></a>Sestavení: System.Workflow.Runtime.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Activities.Statements.Interop>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br />Typy Workflow Foundation 3.0 jsou zastaralé. Místo toho použijte typy Workflow 4.0 z <xref:System.Activities>.\*.|
|<xref:System.Activities.Tracking.InteropTrackingRecord>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br />Typy Workflow Foundation 3.0 jsou zastaralé. Místo toho použijte typy Workflow 4.0 z <xref:System.Activities>.\*.|
|Všechny typy v <xref:System.Workflow.Runtime> obor názvů|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|Všechny typy v <xref:System.Workflow.Runtime.Configuration> obor názvů|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|Všechny typy v <xref:System.Workflow.Runtime.DebugEngine> oboru názvů s výjimkou <xref:System.Workflow.Runtime.DebugEngine.DebugEngineCallback>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|Všechny typy v <xref:System.Workflow.Runtime.Hosting> oboru názvů s výjimkou <xref:System.Workflow.Runtime.Hosting.WorkflowCommitWorkBatchService.CommitWorkBatchCallback>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|
|Všechny typy v <xref:System.Workflow.Runtime.Tracking> obor názvů|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> System.Workflow. \* typy se považují za zastaralé. Místo toho použijte nové typy z <xref:System.Activities>.\*.|

 [Zpět na začátek](#introduction)

<a name="workflowservices"></a>
### <a name="assembly-systemworkflowservicesdll"></a>Assembly: System.WorkflowServices.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.ServiceModel.WorkflowServiceHost?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Activation.WorkflowServiceHostFactory?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Activities.Description.WorkflowRuntimeEndpoint?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Configuration.ExtendedWorkflowRuntimeServiceElementCollection?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Configuration.PersistenceProviderElement?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Configuration.WorkflowRuntimeElement?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Description.DurableOperationAttribute?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Description.DurableServiceAttribute?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Description.PersistenceProviderBehavior?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Description.UnknownExceptionAction?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Description.WorkflowRuntimeBehavior?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Dispatcher.DurableOperationContext?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.InstanceLockException?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.InstanceNotFoundException?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.LockingPersistenceProvider?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.PersistenceException?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.PersistenceProvider?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.PersistenceProviderFactory?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|Všechny typy v <xref:System.Workflow.Activities?displayProperty=nameWithType> obor názvů|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|
|<xref:System.Workflow.Runtime.Hosting.ChannelManagerService?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> WF 3 typy jsou zastaralé. Místo toho použijte nové WF 4 typy z <xref:System.Activities>.\*.|

 [Zpět na začátek](#introduction)

<a name="xaml"></a>
### <a name="assembly-systemxamldll"></a>Assembly: System.Xaml.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute?displayProperty=nameWithType>|To není používán analyzátoru XAML. Podívejte se prosím na <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=nameWithType>.|

 [Zpět na začátek](#introduction)

<a name="xml"></a>
### <a name="assembly-systemxmldll"></a>Assembly: System.Xml.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Xml.IApplicationResourceStreamResolver?displayProperty=nameWithType>|Nejprve zastaralé v rozhraní .NET Framework 4.5.<br /><br /> Použití tohoto typu vygeneruje chybu kompilátoru.<br /><br /> Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Xml.Schema.XmlSchemaCollection?displayProperty=nameWithType>|Použití <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> pro kompilaci schématu a ověřování.|
|<xref:System.Xml.XmlValidatingReader?displayProperty=nameWithType>|Použití <xref:System.Xml.XmlReader?displayProperty=nameWithType> vytvořené <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> metodu pomocí odpovídající <xref:System.Xml.XmlReaderSettings?displayProperty=nameWithType> místo.|
|<xref:System.Xml.XmlXapResolver?displayProperty=nameWithType>|Použití tohoto typu vygeneruje chybu kompilátoru. Toto rozhraní API podporuje infrastrukturu rozhraní .NET Framework a není určeno pro použití přímo v kódu.|
|<xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>|Tato třída je zastaralá. Použijte prosím <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType> místo.|

 [Zpět na začátek](#introduction)

<a name="WindowsBase"></a>
### <a name="assembly-windowsbasedll"></a>Sestavení: knihovně WindowsBase.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType>|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType> se už nepoužívá. Toto rozhraní je již používán.|

 [Zpět na začátek](#introduction)

<a name="obsolete_types_in_microsoft_assemblies"></a>
## <a name="obsolete-types-in-microsoft-assemblies"></a>Zastaralé typy v sestavení společnosti Microsoft
 V následujících částech jsou zastaralé typy v sestavení společnosti Microsoft. Tato sestavení se speciálním účelem sestavení, jako je například sestavení, které se zaměřují jednotlivých jazyků (například jako Microsoft.VisualC.dll nebo Microsoft.JScript.dll).

<a name="IEHost"></a>
### <a name="assembly-iehostdll-and-ieexecexe"></a>Sestavení: IEHost.dll a IEExec.exe
 Sestavení IEHost.dll a IEExec.exe byly odebrány z rozhraní .NET Framework. Všechny jejich typy a členové jsou zastaralé a od verze se nepodporují [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Tato sestavení byly použity k hostování ovládacích prvků Windows Forms a ke spuštění spustitelných souborů v aplikaci Internet Explorer. Doporučené alternativy patří ClickOnce, aplikace prohlížeče XAML (XBAP) a Microsoft Silverlight.

 [Zpět na začátek](#introduction)

<a name="Engine"></a>
### <a name="assembly-microsoftbuildenginedll"></a>Sestavení: Microsoft.Build.Engine.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=nameWithType>|Tato třída je zastaralá. Použijte prosím <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> z *Microsoft.Build* sestavení místo toho.|
|<xref:Microsoft.Build.BuildEngine.Project?displayProperty=nameWithType>|Tato třída je zastaralá. Použijte prosím <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> z *Microsoft.Build* sestavení místo toho.|

 [Zpět na začátek](#introduction)

<a name="jscript"></a>
### <a name="assembly-microsoftjscriptdll"></a>Assembly: Microsoft.JScript.dll

|Typ|Zpráva|
|----------|-------------|
|<xref:Microsoft.JScript.Vsa.BaseVsaEngine?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.BaseVsaSite?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.BaseVsaStartup?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaCodeItem?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaEngine?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaError?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaGlobalItem?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItem?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItems?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaPersistSite?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaReferenceItem?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.IJSVsaSite?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.JSVsaError?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.JSVsaException?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemFlag?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemType?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.ResInfo?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|
|<xref:Microsoft.JScript.Vsa.VsaEngine?displayProperty=nameWithType>|Tento typ se přestala nabízet v sadě Visual Studio 2005; nebude ničím nahrazen pro tuto funkci. Podrobnosti najdete <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> dokumentaci o další pomoc.|

 [Zpět na začátek](#introduction)

<a name="VBCompat"></a>
### <a name="assembly-microsoftvisualbasiccompatibilitydll"></a>Sestavení: Microsoft.VisualBasic.Compatibility.dll
  Informace o migraci z jazyka Visual Basic 6 najdete v tématu [jazyka Visual Basic 6.0 Resource Center](https://msdn.microsoft.com/library/windows/desktop/ms788229).
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
|<xref:Microsoft.VisualC.DebugInfoInPDBAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll je sestavení zastaralé a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.DecoratedNameAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll je sestavení zastaralé a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.IsConstModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je sestavení zastaralé a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.IsCXXReferenceModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je sestavení zastaralé a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.IsLongModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je sestavení zastaralé a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.IsSignedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je sestavení zastaralé a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.IsVolatileModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je sestavení zastaralé a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.MiscellaneousBitsAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll je sestavení zastaralé a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.NeedsCopyConstructorModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je sestavení zastaralé a existuje pouze pro zpětnou kompatibilitu.|
|<xref:Microsoft.VisualC.NoSignSpecifiedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll je sestavení zastaralé a existuje pouze pro zpětnou kompatibilitu.|

## <a name="see-also"></a>Viz také
 [Co je zastaralé v knihovně tříd](../../../docs/framework/whats-new/whats-obsolete.md) [zastaralé členy](../../../docs/framework/whats-new/obsolete-members.md)
