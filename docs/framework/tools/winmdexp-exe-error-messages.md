---
title: Chybové zprávy nástroje Winmdexp.exe
description: Pochopení Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime) – chybové zprávy, které se zobrazí pouze během procesu sestavení, pokud je kompilace .NET úspěšná.
ms.date: 03/30/2017
f1_keywords:
- WME1095
- WME1110
- WME15
- WME1094
- WME1078
- WME1080
- WME1014
- WME1025
- WME1089
- WME1111
- WME1010
- WME1013
- WME1055
- WME1005
- WME1033
- WME1003
- WME1011
- WME1046
- WME0013
- WME1032
- WME1029
- WME1048
- WME1019
- WME1106
- WME0012
- WME1017
- WME1098
- WME1039
- WME20
- WME1006
- WME1088
- WME0004
- WME10
- WME12
- WME0015
- WME0017
- WME1026
- WME1045
- WME1002
- WME1051
- WME1107
- WME1100
- WME1072
- WME1090
- WME1105
- WME1022
- WME11
- WME17
- WME1063
- WME1041
- WME1057
- WME1037
- WME1007
- WME3
- WME1096
- WME0003
- WME0006
- WME1065
- WME1102
- WME1070
- WME1113
- WME1064
- WME1061
- WME1066
- WME1018
- WME1049
- WME1027
- WME1101
- WME1058
- WME0005
- WME1083
- WME1004
- WME1073
- WME1087
- WME1077
- WME19
- WME1086
- WME1085
- WME1040
- WME8
- WME1081
- WME1023
- WME4
- WME1050
- WME7
- WME1091
- WME14
- WME0007
- WME1024
- WME1012
- WME1036
- WME0010
- WME1104
- WME1035
- WME1021
- WME1075
- WME5
- WME13
- WME1074
- WME1028
- WME0014
- WME1030
- WME1008
- WME1052
- WME1079
- WME1054
- WME1093
- WME1042
- WME2
- WME1062
- WME6
- WME1001
- WME0011
- WME16
- WME0001
- WME1020
- WME1084
- WME1103
- WME1092
- WME1
- WME0002
- WME1112
- WME1016
- WME1060
- WME0008
- WME0016
- WME1097
- WME1034
- WME1108
- WME1082
- WME1099
- WME1069
- WME1031
- WME1009
- WME1068
- WME1067
- WME1059
- WME18
- WME1038
- WME0009
- WME1109
- WME1056
- WME1076
- WME1071
- WME1044
- WME1043
- WME1053
- WME1015
- WME1047
- WME9
helpviewer_keywords:
- Winmdexp.exe, error messages
- Windows Runtime Metadata Export Tool, error messages
- error messages, Winmdexp.exe
ms.assetid: 8271973c-deba-47a6-8e5e-04ce63f146ad
ms.openlocfilehash: 1b44273bd5a8868ba426d9ac0eabbefcb725e70f
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325604"
---
# <a name="winmdexpexe-error-messages"></a>Chybové zprávy nástroje Winmdexp.exe

Proces sestavení volá [Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)](winmdexp-exe-windows-runtime-metadata-export-tool.md) při použití šablony **prostředí Windows Runtime komponenty** v aplikaci Visual Studio 2012, takže Winmdexp.exe chybové zprávy se zobrazí v **Seznam chyb**. Winmdexp.exe funguje v modulu, který je zkompilován s `/target:winmdobj` možností. Protože vyžaduje zkompilovaný modul jako vstup, jeho chybové zprávy se nezobrazí, pokud kompilace nebude úspěšná.  
  
 Chybové zprávy jsou navržené tak, aby obsahovaly všechny informace, které potřebujete k vyřešení chybových podmínek, které jsou vykazují. Některé problémy ale vyžadují více informací, než se bude vejít do zprávy. Další informace najdete v [části diagnostikování prostředí Windows runtimech chybových podmínek komponent](https://docs.microsoft.com/previous-versions/hh977010(v=vs.110)).  
  
 Pokud vaše chyba není popsána v tomto článku a máte pocit, že zpráva neobsahuje dostatečné informace k vyřešení problému, použijte odkaz na zpětnou vazbu v tomto článku a přidejte chybovou zprávu. Případně můžete vytvořit chybu na [webu komunity vývojářů](https://developercommunity.visualstudio.com/). Můžete se také podívat na Další informace o [fórech Microsoftu](https://social.msdn.microsoft.com/Forums/).  
  
## <a name="see-also"></a>Viz také

- [Winmdexp.exe (Nástroj pro export metadat prostředí Windows Runtime)](winmdexp-exe-windows-runtime-metadata-export-tool.md)
- [Diagnostikování chybových podmínek součásti prostředí Windows Runtime](https://docs.microsoft.com/previous-versions/hh977010(v=vs.110))
