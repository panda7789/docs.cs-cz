---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: e3edd7f7080562d03453898dba7a9326561803b5
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124192"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Aplikace, které hostují obsah [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] přes PresentationHost. exe, implementují toto rozhraní, aby poskytovaly bod integrace mezi hostitelem a PresentationHost. exe.  
  
## <a name="remarks"></a>Poznámky  
 Aplikace Win32, jako jsou například webové prohlížeče, mohou hostovat obsah WPF, včetně aplikací prohlížeče XAML (XBAP) a volně XAML. Pro hostování obsahu WPF aplikace Win32 vytvoří instanci [ovládacího prvku WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)). Aby bylo možné hostovat, WPF vytvoří instanci PresentationHost. exe, která poskytne hostovanému obsahu WPF na hostitele pro zobrazení v [ovládacím prvku WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752040(v=vs.85)).  
  
 Integrace povolená nástrojem `IWpfHostSupport` umožňuje PresentationHost. exe:  
  
- Vyhledejte a zaregistrujte se nezpracovanými vstupními zařízeními (zařízení s lidskými rozhraními), na které má hostitelská aplikace zájem.  
  
- Přijímat vstupní zprávy z registrovaných nezpracovaných vstupních zařízení a předají příslušné zprávy do hostitelské aplikace.  
  
- Dotazování hostitelské aplikace na vlastní průběh a chybná uživatelská rozhraní.  
  
> [!NOTE]
> Toto rozhraní API je zamýšlené a podporované jenom pro použití v místním klientském počítači.  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|Umožňuje PresentationHost. exe zjistit nezpracované vstupní zařízení (zařízení s lidskými rozhraními), na které hostitelská aplikace zajímá.|  
|[FilterInputMessage](filterinputmessage.md)|Volá se PresentationHost. exe při každém přijetí zprávy, pokud se nevrátí E_NOTIMPL.|  
|[GetCustomUI](getcustomui.md)|Ve výchozím nastavení poskytuje PresentationHost. exe vlastní průběh nasazení a uživatelská rozhraní chyby nasazení, která se zobrazí při nasazení obsahu WPF.|
