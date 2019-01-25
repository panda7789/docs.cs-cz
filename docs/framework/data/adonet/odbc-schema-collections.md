---
title: Kolekce schémat ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: 072a9cd365031cd5660d1824bc229d459abc5af8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525830"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="4cc5a-102">Kolekce schémat ODBC</span><span class="sxs-lookup"><span data-stu-id="4cc5a-102">ODBC Schema Collections</span></span>
<span data-ttu-id="4cc5a-103">Tato část popisuje kolekci podpora schématu pro ovladače ODBC pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="4cc5a-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="4cc5a-104">Ovladač ODBC Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="4cc5a-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="4cc5a-105">Ovladače ODBC Microsoft SQL Server podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="4cc5a-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="4cc5a-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="4cc5a-106">Tables</span></span>  
  
-   <span data-ttu-id="4cc5a-107">Indexy</span><span class="sxs-lookup"><span data-stu-id="4cc5a-107">Indexes</span></span>  
  
-   <span data-ttu-id="4cc5a-108">Sloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-108">Columns</span></span>  
  
-   <span data-ttu-id="4cc5a-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="4cc5a-109">Procedures</span></span>  
  
-   <span data-ttu-id="4cc5a-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4cc5a-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="4cc5a-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4cc5a-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="4cc5a-112">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="4cc5a-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="4cc5a-113">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="4cc5a-113">Tables and Views</span></span>  
  
|<span data-ttu-id="4cc5a-114">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-114">ColumnName</span></span>|<span data-ttu-id="4cc5a-115">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="4cc5a-116">TABLE_CAT</span></span>|<span data-ttu-id="4cc5a-117">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-117">String</span></span>|  
|<span data-ttu-id="4cc5a-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4cc5a-118">TABLE_SCHEM</span></span>|<span data-ttu-id="4cc5a-119">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-119">String</span></span>|  
|<span data-ttu-id="4cc5a-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-120">TABLE_NAME</span></span>|<span data-ttu-id="4cc5a-121">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-121">String</span></span>|  
|<span data-ttu-id="4cc5a-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-122">TABLE_TYPE</span></span>|<span data-ttu-id="4cc5a-123">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-123">String</span></span>|  
|<span data-ttu-id="4cc5a-124">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-124">REMARKS</span></span>|<span data-ttu-id="4cc5a-125">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="4cc5a-126">Indexy</span><span class="sxs-lookup"><span data-stu-id="4cc5a-126">Indexes</span></span>  
  
|<span data-ttu-id="4cc5a-127">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-127">ColumnName</span></span>|<span data-ttu-id="4cc5a-128">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="4cc5a-129">TABLE_CAT</span></span>|<span data-ttu-id="4cc5a-130">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-130">String</span></span>|  
|<span data-ttu-id="4cc5a-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4cc5a-131">TABLE_SCHEM</span></span>|<span data-ttu-id="4cc5a-132">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-132">String</span></span>|  
|<span data-ttu-id="4cc5a-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-133">TABLE_NAME</span></span>|<span data-ttu-id="4cc5a-134">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-134">String</span></span>|  
|<span data-ttu-id="4cc5a-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-135">NON_UNIQUE</span></span>|<span data-ttu-id="4cc5a-136">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-136">Int16</span></span>|  
|<span data-ttu-id="4cc5a-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="4cc5a-138">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-138">String</span></span>|  
|<span data-ttu-id="4cc5a-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-139">INDEX_NAME</span></span>|<span data-ttu-id="4cc5a-140">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-140">String</span></span>|  
|<span data-ttu-id="4cc5a-141">TYP</span><span class="sxs-lookup"><span data-stu-id="4cc5a-141">TYPE</span></span>|<span data-ttu-id="4cc5a-142">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-142">Int16</span></span>|  
|<span data-ttu-id="4cc5a-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4cc5a-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="4cc5a-144">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-144">Int16</span></span>|  
|<span data-ttu-id="4cc5a-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-145">COLUMN_NAME</span></span>|<span data-ttu-id="4cc5a-146">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-146">String</span></span>|  
|<span data-ttu-id="4cc5a-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="4cc5a-147">ASC_OR_DESC</span></span>|<span data-ttu-id="4cc5a-148">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-148">String</span></span>|  
|<span data-ttu-id="4cc5a-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-149">CARDINATLITY</span></span>|<span data-ttu-id="4cc5a-150">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-150">Int32</span></span>|  
|<span data-ttu-id="4cc5a-151">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-151">PAGES</span></span>|<span data-ttu-id="4cc5a-152">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-152">Int32</span></span>|  
|<span data-ttu-id="4cc5a-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="4cc5a-153">FILTER_CONDITION</span></span>|<span data-ttu-id="4cc5a-154">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-154">String</span></span>|  
|<span data-ttu-id="4cc5a-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4cc5a-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="4cc5a-156">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-156">String</span></span>|  
|<span data-ttu-id="4cc5a-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-158">Byte</span><span class="sxs-lookup"><span data-stu-id="4cc5a-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="4cc5a-159">Sloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-159">Columns</span></span>  
  
|<span data-ttu-id="4cc5a-160">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-160">ColumnName</span></span>|<span data-ttu-id="4cc5a-161">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="4cc5a-162">TABLE_CAT</span></span>|<span data-ttu-id="4cc5a-163">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-163">String</span></span>|  
|<span data-ttu-id="4cc5a-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4cc5a-164">TABLE_SCHEM</span></span>|<span data-ttu-id="4cc5a-165">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-165">String</span></span>|  
|<span data-ttu-id="4cc5a-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-166">TABLE_NAME</span></span>|<span data-ttu-id="4cc5a-167">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-167">String</span></span>|  
|<span data-ttu-id="4cc5a-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-168">COLUMN_NAME</span></span>|<span data-ttu-id="4cc5a-169">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-169">String</span></span>|  
|<span data-ttu-id="4cc5a-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-170">DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-171">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-171">Int16</span></span>|  
|<span data-ttu-id="4cc5a-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-172">TYPE_NAME</span></span>|<span data-ttu-id="4cc5a-173">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-173">String</span></span>|  
|<span data-ttu-id="4cc5a-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-174">COLUMN_SIZE</span></span>|<span data-ttu-id="4cc5a-175">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-175">Int32</span></span>|  
|<span data-ttu-id="4cc5a-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4cc5a-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="4cc5a-177">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-177">Int32</span></span>|  
|<span data-ttu-id="4cc5a-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="4cc5a-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="4cc5a-179">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-179">Int16</span></span>|  
|<span data-ttu-id="4cc5a-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="4cc5a-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="4cc5a-181">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-181">Int16</span></span>|  
|<span data-ttu-id="4cc5a-182">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="4cc5a-182">NULLABLE</span></span>|<span data-ttu-id="4cc5a-183">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-183">Int16</span></span>|  
|<span data-ttu-id="4cc5a-184">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-184">REMARKS</span></span>|<span data-ttu-id="4cc5a-185">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-185">String</span></span>|  
|<span data-ttu-id="4cc5a-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="4cc5a-186">COLUMN_DEF</span></span>|<span data-ttu-id="4cc5a-187">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-187">String</span></span>|  
|<span data-ttu-id="4cc5a-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-189">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-189">Int16</span></span>|  
|<span data-ttu-id="4cc5a-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="4cc5a-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="4cc5a-191">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-191">Int16</span></span>|  
|<span data-ttu-id="4cc5a-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4cc5a-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="4cc5a-193">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-193">Int32</span></span>|  
|<span data-ttu-id="4cc5a-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4cc5a-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="4cc5a-195">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-195">Int32</span></span>|  
|<span data-ttu-id="4cc5a-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-196">IS_NULLABLE</span></span>|<span data-ttu-id="4cc5a-197">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-197">String</span></span>|  
|<span data-ttu-id="4cc5a-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4cc5a-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="4cc5a-199">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-199">String</span></span>|  
|<span data-ttu-id="4cc5a-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4cc5a-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="4cc5a-201">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-201">String</span></span>|  
|<span data-ttu-id="4cc5a-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-203">Byte</span><span class="sxs-lookup"><span data-stu-id="4cc5a-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="4cc5a-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="4cc5a-204">Procedures</span></span>  
  
|<span data-ttu-id="4cc5a-205">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-205">ColumnName</span></span>|<span data-ttu-id="4cc5a-206">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="4cc5a-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="4cc5a-208">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-208">String</span></span>|  
|<span data-ttu-id="4cc5a-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4cc5a-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="4cc5a-210">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-210">String</span></span>|  
|<span data-ttu-id="4cc5a-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="4cc5a-212">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-212">String</span></span>|  
|<span data-ttu-id="4cc5a-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4cc5a-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="4cc5a-214">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-214">Int32</span></span>|  
|<span data-ttu-id="4cc5a-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4cc5a-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="4cc5a-216">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-216">Int32</span></span>|  
|<span data-ttu-id="4cc5a-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="4cc5a-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="4cc5a-218">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-218">Int32</span></span>|  
|<span data-ttu-id="4cc5a-219">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-219">REMARKS</span></span>|<span data-ttu-id="4cc5a-220">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-220">String</span></span>|  
|<span data-ttu-id="4cc5a-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="4cc5a-222">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="4cc5a-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4cc5a-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="4cc5a-224">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-224">ColumnName</span></span>|<span data-ttu-id="4cc5a-225">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="4cc5a-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="4cc5a-227">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-227">String</span></span>|  
|<span data-ttu-id="4cc5a-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4cc5a-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="4cc5a-229">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-229">String</span></span>|  
|<span data-ttu-id="4cc5a-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="4cc5a-231">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-231">String</span></span>|  
|<span data-ttu-id="4cc5a-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-232">COLUMN_NAME</span></span>|<span data-ttu-id="4cc5a-233">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-233">String</span></span>|  
|<span data-ttu-id="4cc5a-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-234">COLUMN_TYPE</span></span>|<span data-ttu-id="4cc5a-235">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-235">Int16</span></span>|  
|<span data-ttu-id="4cc5a-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-236">DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-237">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-237">Int16</span></span>|  
|<span data-ttu-id="4cc5a-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-238">TYPE_NAME</span></span>|<span data-ttu-id="4cc5a-239">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-239">String</span></span>|  
|<span data-ttu-id="4cc5a-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-240">COLUMN_SIZE</span></span>|<span data-ttu-id="4cc5a-241">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-241">Int32</span></span>|  
|<span data-ttu-id="4cc5a-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4cc5a-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="4cc5a-243">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-243">Int32</span></span>|  
|<span data-ttu-id="4cc5a-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="4cc5a-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="4cc5a-245">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-245">Int16</span></span>|  
|<span data-ttu-id="4cc5a-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="4cc5a-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="4cc5a-247">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-247">Int16</span></span>|  
|<span data-ttu-id="4cc5a-248">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="4cc5a-248">NULLABLE</span></span>|<span data-ttu-id="4cc5a-249">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-249">Int16</span></span>|  
|<span data-ttu-id="4cc5a-250">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-250">REMARKS</span></span>|<span data-ttu-id="4cc5a-251">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-251">String</span></span>|  
|<span data-ttu-id="4cc5a-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="4cc5a-252">COLUMN_DEF</span></span>|<span data-ttu-id="4cc5a-253">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-253">String</span></span>|  
|<span data-ttu-id="4cc5a-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-255">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-255">Int16</span></span>|  
|<span data-ttu-id="4cc5a-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="4cc5a-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="4cc5a-257">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-257">Int16</span></span>|  
|<span data-ttu-id="4cc5a-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4cc5a-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="4cc5a-259">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-259">Int32</span></span>|  
|<span data-ttu-id="4cc5a-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4cc5a-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="4cc5a-261">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-261">Int32</span></span>|  
|<span data-ttu-id="4cc5a-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-262">IS_NULLABLE</span></span>|<span data-ttu-id="4cc5a-263">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-263">String</span></span>|  
|<span data-ttu-id="4cc5a-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4cc5a-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="4cc5a-265">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-265">String</span></span>|  
|<span data-ttu-id="4cc5a-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4cc5a-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="4cc5a-267">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-267">String</span></span>|  
|<span data-ttu-id="4cc5a-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-269">Byte</span><span class="sxs-lookup"><span data-stu-id="4cc5a-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="4cc5a-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4cc5a-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="4cc5a-271">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-271">ColumnName</span></span>|<span data-ttu-id="4cc5a-272">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="4cc5a-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="4cc5a-274">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-274">String</span></span>|  
|<span data-ttu-id="4cc5a-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4cc5a-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="4cc5a-276">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-276">String</span></span>|  
|<span data-ttu-id="4cc5a-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="4cc5a-278">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-278">String</span></span>|  
|<span data-ttu-id="4cc5a-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-279">COLUMN_NAME</span></span>|<span data-ttu-id="4cc5a-280">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-280">String</span></span>|  
|<span data-ttu-id="4cc5a-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-281">COLUMN_TYPE</span></span>|<span data-ttu-id="4cc5a-282">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-282">Int16</span></span>|  
|<span data-ttu-id="4cc5a-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-283">DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-284">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-284">Int16</span></span>|  
|<span data-ttu-id="4cc5a-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-285">TYPE_NAME</span></span>|<span data-ttu-id="4cc5a-286">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-286">String</span></span>|  
|<span data-ttu-id="4cc5a-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-287">COLUMN_SIZE</span></span>|<span data-ttu-id="4cc5a-288">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-288">Int32</span></span>|  
|<span data-ttu-id="4cc5a-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4cc5a-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="4cc5a-290">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-290">Int32</span></span>|  
|<span data-ttu-id="4cc5a-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="4cc5a-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="4cc5a-292">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-292">Int16</span></span>|  
|<span data-ttu-id="4cc5a-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="4cc5a-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="4cc5a-294">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-294">Int16</span></span>|  
|<span data-ttu-id="4cc5a-295">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="4cc5a-295">NULLABLE</span></span>|<span data-ttu-id="4cc5a-296">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-296">Int16</span></span>|  
|<span data-ttu-id="4cc5a-297">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-297">REMARKS</span></span>|<span data-ttu-id="4cc5a-298">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-298">String</span></span>|  
|<span data-ttu-id="4cc5a-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="4cc5a-299">COLUMN_DEF</span></span>|<span data-ttu-id="4cc5a-300">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-300">String</span></span>|  
|<span data-ttu-id="4cc5a-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-302">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-302">Int16</span></span>|  
|<span data-ttu-id="4cc5a-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="4cc5a-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="4cc5a-304">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-304">Int16</span></span>|  
|<span data-ttu-id="4cc5a-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4cc5a-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="4cc5a-306">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-306">Int32</span></span>|  
|<span data-ttu-id="4cc5a-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4cc5a-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="4cc5a-308">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-308">Int32</span></span>|  
|<span data-ttu-id="4cc5a-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-309">IS_NULLABLE</span></span>|<span data-ttu-id="4cc5a-310">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-310">String</span></span>|  
|<span data-ttu-id="4cc5a-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="4cc5a-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="4cc5a-312">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-312">String</span></span>|  
|<span data-ttu-id="4cc5a-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="4cc5a-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="4cc5a-314">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-314">String</span></span>|  
|<span data-ttu-id="4cc5a-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-316">Byte</span><span class="sxs-lookup"><span data-stu-id="4cc5a-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="4cc5a-317">Ovladač ODBC Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="4cc5a-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="4cc5a-318">Ovladače ODBC Microsoft SQL Server Oracle podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="4cc5a-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="4cc5a-319">Tabulky</span><span class="sxs-lookup"><span data-stu-id="4cc5a-319">Tables</span></span>  
  
-   <span data-ttu-id="4cc5a-320">Sloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-320">Columns</span></span>  
  
-   <span data-ttu-id="4cc5a-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="4cc5a-321">Procedures</span></span>  
  
-   <span data-ttu-id="4cc5a-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4cc5a-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="4cc5a-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4cc5a-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="4cc5a-324">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="4cc5a-324">Views</span></span>  
  
-   <span data-ttu-id="4cc5a-325">Indexy</span><span class="sxs-lookup"><span data-stu-id="4cc5a-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="4cc5a-326">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="4cc5a-326">Tables and Views</span></span>  
  
|<span data-ttu-id="4cc5a-327">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-327">ColumnName</span></span>|<span data-ttu-id="4cc5a-328">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="4cc5a-330">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-330">String</span></span>|  
|<span data-ttu-id="4cc5a-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-331">TABLE_OWNER</span></span>|<span data-ttu-id="4cc5a-332">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-332">String</span></span>|  
|<span data-ttu-id="4cc5a-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-333">TABLE_NAME</span></span>|<span data-ttu-id="4cc5a-334">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-334">String</span></span>|  
|<span data-ttu-id="4cc5a-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-335">TABLE_TYPE</span></span>|<span data-ttu-id="4cc5a-336">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-336">String</span></span>|  
|<span data-ttu-id="4cc5a-337">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-337">REMARKS</span></span>|<span data-ttu-id="4cc5a-338">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="4cc5a-339">Sloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-339">Columns</span></span>  
  
|<span data-ttu-id="4cc5a-340">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-340">ColumnName</span></span>|<span data-ttu-id="4cc5a-341">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="4cc5a-343">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-343">String</span></span>|  
|<span data-ttu-id="4cc5a-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-344">TABLE_OWNER</span></span>|<span data-ttu-id="4cc5a-345">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-345">String</span></span>|  
|<span data-ttu-id="4cc5a-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-346">TABLE_NAME</span></span>|<span data-ttu-id="4cc5a-347">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-347">String</span></span>|  
|<span data-ttu-id="4cc5a-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-348">COLUMN_NAME</span></span>|<span data-ttu-id="4cc5a-349">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-349">String</span></span>|  
|<span data-ttu-id="4cc5a-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-350">DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-351">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-351">Int16</span></span>|  
|<span data-ttu-id="4cc5a-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-352">TYPE_NAME</span></span>|<span data-ttu-id="4cc5a-353">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-353">String</span></span>|  
|<span data-ttu-id="4cc5a-354">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="4cc5a-354">PRECISION</span></span>|<span data-ttu-id="4cc5a-355">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-355">Int32</span></span>|  
|<span data-ttu-id="4cc5a-356">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="4cc5a-356">LENGTH</span></span>|<span data-ttu-id="4cc5a-357">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-357">Int32</span></span>|  
|<span data-ttu-id="4cc5a-358">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="4cc5a-358">SCALE</span></span>|<span data-ttu-id="4cc5a-359">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-359">Int16</span></span>|  
|<span data-ttu-id="4cc5a-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="4cc5a-360">RADIX</span></span>|<span data-ttu-id="4cc5a-361">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-361">Int16</span></span>|  
|<span data-ttu-id="4cc5a-362">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="4cc5a-362">NULLABLE</span></span>|<span data-ttu-id="4cc5a-363">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-363">Int16</span></span>|  
|<span data-ttu-id="4cc5a-364">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-364">REMARKS</span></span>|<span data-ttu-id="4cc5a-365">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-365">String</span></span>|  
|<span data-ttu-id="4cc5a-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4cc5a-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="4cc5a-367">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="4cc5a-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="4cc5a-368">Procedures</span></span>  
  
|<span data-ttu-id="4cc5a-369">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-369">ColumnName</span></span>|<span data-ttu-id="4cc5a-370">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="4cc5a-372">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-372">String</span></span>|  
|<span data-ttu-id="4cc5a-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="4cc5a-374">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-374">String</span></span>|  
|<span data-ttu-id="4cc5a-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="4cc5a-376">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-376">String</span></span>|  
|<span data-ttu-id="4cc5a-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4cc5a-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="4cc5a-378">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-378">Int16</span></span>|  
|<span data-ttu-id="4cc5a-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4cc5a-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="4cc5a-380">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-380">Int16</span></span>|  
|<span data-ttu-id="4cc5a-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="4cc5a-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="4cc5a-382">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-382">Int16</span></span>|  
|<span data-ttu-id="4cc5a-383">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-383">REMARKS</span></span>|<span data-ttu-id="4cc5a-384">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-384">String</span></span>|  
|<span data-ttu-id="4cc5a-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="4cc5a-386">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="4cc5a-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4cc5a-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="4cc5a-388">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-388">ColumnName</span></span>|<span data-ttu-id="4cc5a-389">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="4cc5a-391">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-391">String</span></span>|  
|<span data-ttu-id="4cc5a-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="4cc5a-393">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-393">String</span></span>|  
|<span data-ttu-id="4cc5a-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="4cc5a-395">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-395">String</span></span>|  
|<span data-ttu-id="4cc5a-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-396">COLUMN_NAME</span></span>|<span data-ttu-id="4cc5a-397">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-397">String</span></span>|  
|<span data-ttu-id="4cc5a-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-398">COLUMN_TYPE</span></span>|<span data-ttu-id="4cc5a-399">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-399">Int16</span></span>|  
|<span data-ttu-id="4cc5a-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-400">DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-401">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-401">Int16</span></span>|  
|<span data-ttu-id="4cc5a-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-402">TYPE_NAME</span></span>|<span data-ttu-id="4cc5a-403">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-403">String</span></span>|  
|<span data-ttu-id="4cc5a-404">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="4cc5a-404">PRECISION</span></span>|<span data-ttu-id="4cc5a-405">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-405">Int32</span></span>|  
|<span data-ttu-id="4cc5a-406">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="4cc5a-406">LENGTH</span></span>|<span data-ttu-id="4cc5a-407">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-407">Int32</span></span>|  
|<span data-ttu-id="4cc5a-408">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="4cc5a-408">SCALE</span></span>|<span data-ttu-id="4cc5a-409">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-409">Int16</span></span>|  
|<span data-ttu-id="4cc5a-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="4cc5a-410">RADIX</span></span>|<span data-ttu-id="4cc5a-411">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-411">Int16</span></span>|  
|<span data-ttu-id="4cc5a-412">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="4cc5a-412">NULLABLE</span></span>|<span data-ttu-id="4cc5a-413">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-413">Int16</span></span>|  
|<span data-ttu-id="4cc5a-414">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-414">REMARKS</span></span>|<span data-ttu-id="4cc5a-415">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-415">String</span></span>|  
|<span data-ttu-id="4cc5a-416">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="4cc5a-416">OVERLOAD</span></span>|<span data-ttu-id="4cc5a-417">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-417">Int32</span></span>|  
|<span data-ttu-id="4cc5a-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4cc5a-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="4cc5a-419">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="4cc5a-420">Ovladač ODBC Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="4cc5a-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="4cc5a-421">Ovladač ODBC Microsoft Jet podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="4cc5a-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="4cc5a-422">Tabulky</span><span class="sxs-lookup"><span data-stu-id="4cc5a-422">Tables</span></span>  
  
-   <span data-ttu-id="4cc5a-423">Indexy</span><span class="sxs-lookup"><span data-stu-id="4cc5a-423">Indexes</span></span>  
  
-   <span data-ttu-id="4cc5a-424">Sloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-424">Columns</span></span>  
  
-   <span data-ttu-id="4cc5a-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="4cc5a-425">Procedures</span></span>  
  
-   <span data-ttu-id="4cc5a-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4cc5a-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="4cc5a-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4cc5a-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="4cc5a-428">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="4cc5a-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="4cc5a-429">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="4cc5a-429">Tables and Views</span></span>  
  
|<span data-ttu-id="4cc5a-430">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-430">ColumnName</span></span>|<span data-ttu-id="4cc5a-431">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="4cc5a-433">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-433">String</span></span>|  
|<span data-ttu-id="4cc5a-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-434">TABLE_OWNER</span></span>|<span data-ttu-id="4cc5a-435">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-435">String</span></span>|  
|<span data-ttu-id="4cc5a-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-436">TABLE_NAME</span></span>|<span data-ttu-id="4cc5a-437">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-437">String</span></span>|  
|<span data-ttu-id="4cc5a-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-438">TABLE_TYPE</span></span>|<span data-ttu-id="4cc5a-439">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-439">String</span></span>|  
|<span data-ttu-id="4cc5a-440">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-440">REMARKS</span></span>|<span data-ttu-id="4cc5a-441">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="4cc5a-442">Sloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-442">Columns</span></span>  
  
|<span data-ttu-id="4cc5a-443">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-443">ColumnName</span></span>|<span data-ttu-id="4cc5a-444">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="4cc5a-446">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-446">String</span></span>|  
|<span data-ttu-id="4cc5a-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-447">TABLE_OWNER</span></span>|<span data-ttu-id="4cc5a-448">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-448">String</span></span>|  
|<span data-ttu-id="4cc5a-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-449">TABLE_NAME</span></span>|<span data-ttu-id="4cc5a-450">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-450">String</span></span>|  
|<span data-ttu-id="4cc5a-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-451">COLUMN_NAME</span></span>|<span data-ttu-id="4cc5a-452">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-452">String</span></span>|  
|<span data-ttu-id="4cc5a-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-453">DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-454">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-454">Int16</span></span>|  
|<span data-ttu-id="4cc5a-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-455">TYPE_NAME</span></span>|<span data-ttu-id="4cc5a-456">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-456">String</span></span>|  
|<span data-ttu-id="4cc5a-457">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="4cc5a-457">PRECISION</span></span>|<span data-ttu-id="4cc5a-458">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-458">Int32</span></span>|  
|<span data-ttu-id="4cc5a-459">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="4cc5a-459">LENGTH</span></span>|<span data-ttu-id="4cc5a-460">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-460">Int32</span></span>|  
|<span data-ttu-id="4cc5a-461">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="4cc5a-461">SCALE</span></span>|<span data-ttu-id="4cc5a-462">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-462">Int16</span></span>|  
|<span data-ttu-id="4cc5a-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="4cc5a-463">RADIX</span></span>|<span data-ttu-id="4cc5a-464">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-464">Int16</span></span>|  
|<span data-ttu-id="4cc5a-465">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="4cc5a-465">NULLABLE</span></span>|<span data-ttu-id="4cc5a-466">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-466">Int16</span></span>|  
|<span data-ttu-id="4cc5a-467">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-467">REMARKS</span></span>|<span data-ttu-id="4cc5a-468">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-468">String</span></span>|  
|<span data-ttu-id="4cc5a-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4cc5a-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="4cc5a-470">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="4cc5a-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="4cc5a-471">Procedures</span></span>  
  
|<span data-ttu-id="4cc5a-472">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-472">ColumnName</span></span>|<span data-ttu-id="4cc5a-473">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="4cc5a-475">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-475">String</span></span>|  
|<span data-ttu-id="4cc5a-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="4cc5a-477">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-477">String</span></span>|  
|<span data-ttu-id="4cc5a-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="4cc5a-479">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-479">String</span></span>|  
|<span data-ttu-id="4cc5a-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4cc5a-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="4cc5a-481">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-481">Int16</span></span>|  
|<span data-ttu-id="4cc5a-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="4cc5a-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="4cc5a-483">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-483">Int16</span></span>|  
|<span data-ttu-id="4cc5a-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="4cc5a-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="4cc5a-485">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-485">Int16</span></span>|  
|<span data-ttu-id="4cc5a-486">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-486">REMARKS</span></span>|<span data-ttu-id="4cc5a-487">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-487">String</span></span>|  
|<span data-ttu-id="4cc5a-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="4cc5a-489">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="4cc5a-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="4cc5a-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="4cc5a-491">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-491">ColumnName</span></span>|<span data-ttu-id="4cc5a-492">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="4cc5a-494">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-494">String</span></span>|  
|<span data-ttu-id="4cc5a-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="4cc5a-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="4cc5a-496">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-496">String</span></span>|  
|<span data-ttu-id="4cc5a-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="4cc5a-498">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-498">String</span></span>|  
|<span data-ttu-id="4cc5a-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-499">COLUMN_NAME</span></span>|<span data-ttu-id="4cc5a-500">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-500">String</span></span>|  
|<span data-ttu-id="4cc5a-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-501">COLUMN_TYPE</span></span>|<span data-ttu-id="4cc5a-502">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-502">Int16</span></span>|  
|<span data-ttu-id="4cc5a-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-503">DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-504">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-504">Int16</span></span>|  
|<span data-ttu-id="4cc5a-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-505">TYPE_NAME</span></span>|<span data-ttu-id="4cc5a-506">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-506">String</span></span>|  
|<span data-ttu-id="4cc5a-507">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="4cc5a-507">PRECISION</span></span>|<span data-ttu-id="4cc5a-508">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-508">Int32</span></span>|  
|<span data-ttu-id="4cc5a-509">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="4cc5a-509">LENGTH</span></span>|<span data-ttu-id="4cc5a-510">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-510">Int32</span></span>|  
|<span data-ttu-id="4cc5a-511">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="4cc5a-511">SCALE</span></span>|<span data-ttu-id="4cc5a-512">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-512">Int16</span></span>|  
|<span data-ttu-id="4cc5a-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="4cc5a-513">RADIX</span></span>|<span data-ttu-id="4cc5a-514">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-514">Int16</span></span>|  
|<span data-ttu-id="4cc5a-515">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="4cc5a-515">NULLABLE</span></span>|<span data-ttu-id="4cc5a-516">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-516">Int16</span></span>|  
|<span data-ttu-id="4cc5a-517">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-517">REMARKS</span></span>|<span data-ttu-id="4cc5a-518">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-518">String</span></span>|  
|<span data-ttu-id="4cc5a-519">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="4cc5a-519">OVERLOAD</span></span>|<span data-ttu-id="4cc5a-520">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-520">Int32</span></span>|  
|<span data-ttu-id="4cc5a-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4cc5a-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="4cc5a-522">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="4cc5a-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="4cc5a-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="4cc5a-524">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="4cc5a-524">ColumnName</span></span>|<span data-ttu-id="4cc5a-525">DataType</span><span class="sxs-lookup"><span data-stu-id="4cc5a-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="4cc5a-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="4cc5a-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="4cc5a-527">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-527">String</span></span>|  
|<span data-ttu-id="4cc5a-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="4cc5a-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="4cc5a-529">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-529">String</span></span>|  
|<span data-ttu-id="4cc5a-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="4cc5a-531">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-531">String</span></span>|  
|<span data-ttu-id="4cc5a-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-532">COLUMN_NAME</span></span>|<span data-ttu-id="4cc5a-533">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-533">String</span></span>|  
|<span data-ttu-id="4cc5a-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-534">COLUMN_TYPE</span></span>|<span data-ttu-id="4cc5a-535">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-535">Int16</span></span>|  
|<span data-ttu-id="4cc5a-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-536">DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-537">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-537">Int16</span></span>|  
|<span data-ttu-id="4cc5a-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="4cc5a-538">TYPE_NAME</span></span>|<span data-ttu-id="4cc5a-539">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-539">String</span></span>|  
|<span data-ttu-id="4cc5a-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-540">COLUMN_SIZE</span></span>|<span data-ttu-id="4cc5a-541">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-541">Int32</span></span>|  
|<span data-ttu-id="4cc5a-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4cc5a-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="4cc5a-543">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-543">Int32</span></span>|  
|<span data-ttu-id="4cc5a-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="4cc5a-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="4cc5a-545">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-545">Int16</span></span>|  
|<span data-ttu-id="4cc5a-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="4cc5a-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="4cc5a-547">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-547">Int16</span></span>|  
|<span data-ttu-id="4cc5a-548">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="4cc5a-548">NULLABLE</span></span>|<span data-ttu-id="4cc5a-549">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-549">Int16</span></span>|  
|<span data-ttu-id="4cc5a-550">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="4cc5a-550">REMARKS</span></span>|<span data-ttu-id="4cc5a-551">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-551">String</span></span>|  
|<span data-ttu-id="4cc5a-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="4cc5a-552">COLUMN_DEF</span></span>|<span data-ttu-id="4cc5a-553">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-553">String</span></span>|  
|<span data-ttu-id="4cc5a-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="4cc5a-555">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-555">Int16</span></span>|  
|<span data-ttu-id="4cc5a-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="4cc5a-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="4cc5a-557">Int16</span><span class="sxs-lookup"><span data-stu-id="4cc5a-557">Int16</span></span>|  
|<span data-ttu-id="4cc5a-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="4cc5a-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="4cc5a-559">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-559">Int32</span></span>|  
|<span data-ttu-id="4cc5a-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="4cc5a-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="4cc5a-561">Int32</span><span class="sxs-lookup"><span data-stu-id="4cc5a-561">Int32</span></span>|  
|<span data-ttu-id="4cc5a-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="4cc5a-562">IS_NULLABLE</span></span>|<span data-ttu-id="4cc5a-563">String</span><span class="sxs-lookup"><span data-stu-id="4cc5a-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4cc5a-564">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cc5a-564">See also</span></span>
- [<span data-ttu-id="4cc5a-565">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="4cc5a-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
