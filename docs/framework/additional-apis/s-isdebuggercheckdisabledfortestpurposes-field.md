---
title: Pole s_isDebuggerCheckDisabledForTestPurposes
ms.date: 03/30/2017
ms.technology:
- dotnet-wpf
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: f490ccb4675a434e3f3336723e321f256b10093d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149173"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a>Pole s_isDebuggerCheckDisabledForTestPurposes

Tato privátní pole v `System.Windows.Diagnostics.VisualDiagnostics` třída se používá sada Visual Studio k určení, zda bude provedena interní kontroly pro aktivní ladicí program.

## <a name="syntax"></a>Syntaxe
  
```csharp  
private static bool s_isDebuggerCheckDisabledForTestPurposes
```
  
> [!WARNING]
>  Rozhraní API v `System.Windows.Diagnostics.VisualDiagnostics` třídy jsou k dispozici, pouze když je aplikace spuštěna v ladicím programu. Nastavte `s_isDebuggerCheckDisabledForTestPurposes` k `true` pro přístup k rozhraní API mimo ladicí program.  
>   
>  Microsoft nepodporuje použití tohoto pole v produkční aplikace za žádných okolností.  

## <a name="requirements"></a>Požadavky

**Namespace:** <xref:System.Windows.Diagnostics>

**Sestavení:** PresentationCore (v PresentationCore.dll)

**Verze rozhraní .NET framework:** Dostupné od verze 4.6.