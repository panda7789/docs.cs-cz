---
title: Reflexe v rozhraní .NET Framework pro aplikace pro Windows Store
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection, Windows Store apps
- .NET for Windows Store apps, TypeInfo class
ms.assetid: 0d07090c-9b47-4ecc-81d1-29d539603c9b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9aaec282fda0a038d14f3a0cd57e1a8a2855f2ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448142"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Reflexe v rozhraní .NET Framework pro aplikace pro Windows Store

Starting with the .NET Framework 4.5, the .NET Framework includes a set of reflection types and members for use in Windows 8.x Store apps. These types and members are available in the full .NET Framework as well as in the .NET for Windows Store apps. Tento dokument popisuje hlavní rozdíly mezi těmito položkami a jejich protějšky v rozhraní .NET Framework 4 a dřívějších verzích.  
  
 If you are creating a Windows 8.x Store app, you must use the reflection types and members in the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Tyto typy a členy jsou také k dispozici, ačkoli nejsou vyžadovány, pro použití v aplikacích pracovní plochy, takže lze použít stejný kód pro oba typy aplikací.  
  
## <a name="typeinfo-and-assembly-loading"></a>TypeInfo a načítání sestavení  
 V rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] třída <xref:System.Reflection.TypeInfo> obsahuje některé funkce třídy <xref:System.Type> rozhraní .NET Framework 4. Objekt <xref:System.Type> představuje odkaz na definici typu, zatímco objekt <xref:System.Reflection.TypeInfo> představuje samotnou definici typu. To umožňuje práci s objekty typu <xref:System.Type> bez toho, aby modul runtime musel načíst sestavení, na které odkazují. Získání přidruženého objektu <xref:System.Reflection.TypeInfo> vynutí načtení sestavení.  
  
 Typ <xref:System.Reflection.TypeInfo> obsahuje mnoho členů, jež jsou k dispozici v typu <xref:System.Type>, a mnoho vlastností reflexe rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] vrací kolekce objektů <xref:System.Reflection.TypeInfo>. Chcete-li získat objekt <xref:System.Reflection.TypeInfo> z objektu <xref:System.Type>, použijte metodu <xref:System.Reflection.IReflectableType.GetTypeInfo%2A>.  
  
## <a name="query-methods"></a>Query Methods  
 V rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] použijte vlastnosti reflexe, které vrací kolekce typu <xref:System.Collections.Generic.IEnumerable%601>, namísto metod, které vrací pole. Kontexty reflexe mohou pro velká sestavení nebo typy implementovat opožděné procházení těchto kolekcí.  
  
 Vlastnosti reflexe vrací pouze metody deklarované pro daný objekt namísto procházení stromu dědičnosti. Kromě toho nelze pro filtrování použít parametry <xref:System.Reflection.BindingFlags>. Namísto toho filtrování probíhá na vrácené kolekci v uživatelském kódu pomocí dotazů LINQ. Pro objekty reflexe modulu runtime (například výsledek výrazu `typeof(Object)`) je procházení stromu dědičnosti provedeno nejlépe prostřednictvím pomocných metod třídy <xref:System.Reflection.RuntimeReflectionExtensions>. Spotřebitelé objektů z vlastních kontextů reflexe nemohou tyto metody použít a musí strom dědičnosti procházet sami.  
  
## <a name="restrictions"></a>Omezení  
 In a Windows 8.x Store app, access to some .NET Framework types and members is restricted. Například pomocí objektu [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] nelze volat metody rozhraní .NET Framework, které nejsou zahrnuty v rozhraní <xref:System.Reflection.MethodInfo>. In addition, certain types and members that are not considered safe within the context of a Windows 8.x Store app are blocked, as are <xref:System.Runtime.InteropServices.Marshal> and <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> members. Toto omezení se týká pouze typů a členů rozhraní .NET Framework. Váš kód nebo kód třetích stran lze volat jako obvykle.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá typy a členy reflexe rozhraní [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] k načtení metod a vlastností typu <xref:System.Globalization.Calendar>, včetně odvozených metod a vlastností. To run this code, paste it into the code file for a Windows 8.x Store page that contains a <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> control named `textblock1` in a project named Reflection. If you paste this code inside a project with a different name, just make sure you change the namespace name to match your project.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Reflexe](reflection.md)
