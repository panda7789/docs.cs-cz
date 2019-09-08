---
title: Kolekce schémat ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: f0240e99d2420b0956d3c144f837b39e094bb78a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794714"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="5e54a-102">Kolekce schémat ODBC</span><span class="sxs-lookup"><span data-stu-id="5e54a-102">ODBC Schema Collections</span></span>

<span data-ttu-id="5e54a-103">Tato část pojednává o podpoře kolekcí schémat pro ovladače ODBC pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="5e54a-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="5e54a-104">Microsoft SQL Server ovladač ODBC</span><span class="sxs-lookup"><span data-stu-id="5e54a-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="5e54a-105">Ovladač Microsoft SQL Server ODBC podporuje kromě běžných kolekcí schémat následující konkrétní kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="5e54a-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="5e54a-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="5e54a-106">Tables</span></span>

- <span data-ttu-id="5e54a-107">Indexy</span><span class="sxs-lookup"><span data-stu-id="5e54a-107">Indexes</span></span>

- <span data-ttu-id="5e54a-108">Sloupce</span><span class="sxs-lookup"><span data-stu-id="5e54a-108">Columns</span></span>

- <span data-ttu-id="5e54a-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="5e54a-109">Procedures</span></span>

- <span data-ttu-id="5e54a-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5e54a-110">ProcedureColumns</span></span>

- <span data-ttu-id="5e54a-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5e54a-111">ProcedureParameters</span></span>

- <span data-ttu-id="5e54a-112">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="5e54a-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="5e54a-113">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="5e54a-113">Tables and Views</span></span>

|<span data-ttu-id="5e54a-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-114">ColumnName</span></span>|<span data-ttu-id="5e54a-115">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="5e54a-116">TABLE_CAT</span></span>|<span data-ttu-id="5e54a-117">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-117">String</span></span>|
|<span data-ttu-id="5e54a-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5e54a-118">TABLE_SCHEM</span></span>|<span data-ttu-id="5e54a-119">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-119">String</span></span>|
|<span data-ttu-id="5e54a-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-120">TABLE_NAME</span></span>|<span data-ttu-id="5e54a-121">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-121">String</span></span>|
|<span data-ttu-id="5e54a-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-122">TABLE_TYPE</span></span>|<span data-ttu-id="5e54a-123">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-123">String</span></span>|
|<span data-ttu-id="5e54a-124">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-124">REMARKS</span></span>|<span data-ttu-id="5e54a-125">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="5e54a-126">Indexy</span><span class="sxs-lookup"><span data-stu-id="5e54a-126">Indexes</span></span>

|<span data-ttu-id="5e54a-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-127">ColumnName</span></span>|<span data-ttu-id="5e54a-128">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="5e54a-129">TABLE_CAT</span></span>|<span data-ttu-id="5e54a-130">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-130">String</span></span>|
|<span data-ttu-id="5e54a-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5e54a-131">TABLE_SCHEM</span></span>|<span data-ttu-id="5e54a-132">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-132">String</span></span>|
|<span data-ttu-id="5e54a-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-133">TABLE_NAME</span></span>|<span data-ttu-id="5e54a-134">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-134">String</span></span>|
|<span data-ttu-id="5e54a-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="5e54a-135">NON_UNIQUE</span></span>|<span data-ttu-id="5e54a-136">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-136">Int16</span></span>|
|<span data-ttu-id="5e54a-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5e54a-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="5e54a-138">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-138">String</span></span>|
|<span data-ttu-id="5e54a-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-139">INDEX_NAME</span></span>|<span data-ttu-id="5e54a-140">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-140">String</span></span>|
|<span data-ttu-id="5e54a-141">TEXTOVÝ</span><span class="sxs-lookup"><span data-stu-id="5e54a-141">TYPE</span></span>|<span data-ttu-id="5e54a-142">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-142">Int16</span></span>|
|<span data-ttu-id="5e54a-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5e54a-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="5e54a-144">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-144">Int16</span></span>|
|<span data-ttu-id="5e54a-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-145">COLUMN_NAME</span></span>|<span data-ttu-id="5e54a-146">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-146">String</span></span>|
|<span data-ttu-id="5e54a-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="5e54a-147">ASC_OR_DESC</span></span>|<span data-ttu-id="5e54a-148">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-148">String</span></span>|
|<span data-ttu-id="5e54a-149">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="5e54a-149">CARDINALITY</span></span>|<span data-ttu-id="5e54a-150">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-150">Int32</span></span>|
|<span data-ttu-id="5e54a-151">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="5e54a-151">PAGES</span></span>|<span data-ttu-id="5e54a-152">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-152">Int32</span></span>|
|<span data-ttu-id="5e54a-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="5e54a-153">FILTER_CONDITION</span></span>|<span data-ttu-id="5e54a-154">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-154">String</span></span>|
|<span data-ttu-id="5e54a-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5e54a-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="5e54a-156">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-156">String</span></span>|
|<span data-ttu-id="5e54a-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="5e54a-158">Byte</span><span class="sxs-lookup"><span data-stu-id="5e54a-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="5e54a-159">Sloupce</span><span class="sxs-lookup"><span data-stu-id="5e54a-159">Columns</span></span>

|<span data-ttu-id="5e54a-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-160">ColumnName</span></span>|<span data-ttu-id="5e54a-161">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="5e54a-162">TABLE_CAT</span></span>|<span data-ttu-id="5e54a-163">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-163">String</span></span>|
|<span data-ttu-id="5e54a-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5e54a-164">TABLE_SCHEM</span></span>|<span data-ttu-id="5e54a-165">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-165">String</span></span>|
|<span data-ttu-id="5e54a-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-166">TABLE_NAME</span></span>|<span data-ttu-id="5e54a-167">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-167">String</span></span>|
|<span data-ttu-id="5e54a-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-168">COLUMN_NAME</span></span>|<span data-ttu-id="5e54a-169">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-169">String</span></span>|
|<span data-ttu-id="5e54a-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-170">DATA_TYPE</span></span>|<span data-ttu-id="5e54a-171">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-171">Int16</span></span>|
|<span data-ttu-id="5e54a-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-172">TYPE_NAME</span></span>|<span data-ttu-id="5e54a-173">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-173">String</span></span>|
|<span data-ttu-id="5e54a-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="5e54a-174">COLUMN_SIZE</span></span>|<span data-ttu-id="5e54a-175">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-175">Int32</span></span>|
|<span data-ttu-id="5e54a-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5e54a-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="5e54a-177">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-177">Int32</span></span>|
|<span data-ttu-id="5e54a-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="5e54a-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="5e54a-179">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-179">Int16</span></span>|
|<span data-ttu-id="5e54a-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="5e54a-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="5e54a-181">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-181">Int16</span></span>|
|<span data-ttu-id="5e54a-182">POVOLENO</span><span class="sxs-lookup"><span data-stu-id="5e54a-182">NULLABLE</span></span>|<span data-ttu-id="5e54a-183">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-183">Int16</span></span>|
|<span data-ttu-id="5e54a-184">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-184">REMARKS</span></span>|<span data-ttu-id="5e54a-185">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-185">String</span></span>|
|<span data-ttu-id="5e54a-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="5e54a-186">COLUMN_DEF</span></span>|<span data-ttu-id="5e54a-187">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-187">String</span></span>|
|<span data-ttu-id="5e54a-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="5e54a-189">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-189">Int16</span></span>|
|<span data-ttu-id="5e54a-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="5e54a-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="5e54a-191">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-191">Int16</span></span>|
|<span data-ttu-id="5e54a-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5e54a-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="5e54a-193">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-193">Int32</span></span>|
|<span data-ttu-id="5e54a-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5e54a-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="5e54a-195">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-195">Int32</span></span>|
|<span data-ttu-id="5e54a-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5e54a-196">IS_NULLABLE</span></span>|<span data-ttu-id="5e54a-197">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-197">String</span></span>|
|<span data-ttu-id="5e54a-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5e54a-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="5e54a-199">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-199">String</span></span>|
|<span data-ttu-id="5e54a-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5e54a-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="5e54a-201">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-201">String</span></span>|
|<span data-ttu-id="5e54a-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="5e54a-203">Byte</span><span class="sxs-lookup"><span data-stu-id="5e54a-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="5e54a-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="5e54a-204">Procedures</span></span>

|<span data-ttu-id="5e54a-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-205">ColumnName</span></span>|<span data-ttu-id="5e54a-206">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="5e54a-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="5e54a-208">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-208">String</span></span>|
|<span data-ttu-id="5e54a-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5e54a-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="5e54a-210">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-210">String</span></span>|
|<span data-ttu-id="5e54a-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="5e54a-212">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-212">String</span></span>|
|<span data-ttu-id="5e54a-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="5e54a-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="5e54a-214">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-214">Int32</span></span>|
|<span data-ttu-id="5e54a-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="5e54a-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="5e54a-216">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-216">Int32</span></span>|
|<span data-ttu-id="5e54a-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="5e54a-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="5e54a-218">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-218">Int32</span></span>|
|<span data-ttu-id="5e54a-219">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-219">REMARKS</span></span>|<span data-ttu-id="5e54a-220">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-220">String</span></span>|
|<span data-ttu-id="5e54a-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5e54a-222">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="5e54a-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5e54a-223">ProcedureColumns</span></span>

|<span data-ttu-id="5e54a-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-224">ColumnName</span></span>|<span data-ttu-id="5e54a-225">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="5e54a-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="5e54a-227">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-227">String</span></span>|
|<span data-ttu-id="5e54a-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5e54a-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="5e54a-229">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-229">String</span></span>|
|<span data-ttu-id="5e54a-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="5e54a-231">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-231">String</span></span>|
|<span data-ttu-id="5e54a-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-232">COLUMN_NAME</span></span>|<span data-ttu-id="5e54a-233">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-233">String</span></span>|
|<span data-ttu-id="5e54a-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-234">COLUMN_TYPE</span></span>|<span data-ttu-id="5e54a-235">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-235">Int16</span></span>|
|<span data-ttu-id="5e54a-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-236">DATA_TYPE</span></span>|<span data-ttu-id="5e54a-237">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-237">Int16</span></span>|
|<span data-ttu-id="5e54a-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-238">TYPE_NAME</span></span>|<span data-ttu-id="5e54a-239">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-239">String</span></span>|
|<span data-ttu-id="5e54a-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="5e54a-240">COLUMN_SIZE</span></span>|<span data-ttu-id="5e54a-241">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-241">Int32</span></span>|
|<span data-ttu-id="5e54a-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5e54a-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="5e54a-243">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-243">Int32</span></span>|
|<span data-ttu-id="5e54a-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="5e54a-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="5e54a-245">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-245">Int16</span></span>|
|<span data-ttu-id="5e54a-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="5e54a-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="5e54a-247">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-247">Int16</span></span>|
|<span data-ttu-id="5e54a-248">POVOLENO</span><span class="sxs-lookup"><span data-stu-id="5e54a-248">NULLABLE</span></span>|<span data-ttu-id="5e54a-249">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-249">Int16</span></span>|
|<span data-ttu-id="5e54a-250">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-250">REMARKS</span></span>|<span data-ttu-id="5e54a-251">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-251">String</span></span>|
|<span data-ttu-id="5e54a-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="5e54a-252">COLUMN_DEF</span></span>|<span data-ttu-id="5e54a-253">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-253">String</span></span>|
|<span data-ttu-id="5e54a-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="5e54a-255">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-255">Int16</span></span>|
|<span data-ttu-id="5e54a-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="5e54a-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="5e54a-257">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-257">Int16</span></span>|
|<span data-ttu-id="5e54a-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5e54a-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="5e54a-259">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-259">Int32</span></span>|
|<span data-ttu-id="5e54a-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5e54a-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="5e54a-261">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-261">Int32</span></span>|
|<span data-ttu-id="5e54a-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5e54a-262">IS_NULLABLE</span></span>|<span data-ttu-id="5e54a-263">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-263">String</span></span>|
|<span data-ttu-id="5e54a-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5e54a-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="5e54a-265">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-265">String</span></span>|
|<span data-ttu-id="5e54a-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5e54a-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="5e54a-267">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-267">String</span></span>|
|<span data-ttu-id="5e54a-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="5e54a-269">Byte</span><span class="sxs-lookup"><span data-stu-id="5e54a-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="5e54a-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5e54a-270">ProcedureParameters</span></span>

|<span data-ttu-id="5e54a-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-271">ColumnName</span></span>|<span data-ttu-id="5e54a-272">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="5e54a-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="5e54a-274">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-274">String</span></span>|
|<span data-ttu-id="5e54a-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5e54a-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="5e54a-276">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-276">String</span></span>|
|<span data-ttu-id="5e54a-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="5e54a-278">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-278">String</span></span>|
|<span data-ttu-id="5e54a-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-279">COLUMN_NAME</span></span>|<span data-ttu-id="5e54a-280">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-280">String</span></span>|
|<span data-ttu-id="5e54a-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-281">COLUMN_TYPE</span></span>|<span data-ttu-id="5e54a-282">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-282">Int16</span></span>|
|<span data-ttu-id="5e54a-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-283">DATA_TYPE</span></span>|<span data-ttu-id="5e54a-284">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-284">Int16</span></span>|
|<span data-ttu-id="5e54a-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-285">TYPE_NAME</span></span>|<span data-ttu-id="5e54a-286">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-286">String</span></span>|
|<span data-ttu-id="5e54a-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="5e54a-287">COLUMN_SIZE</span></span>|<span data-ttu-id="5e54a-288">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-288">Int32</span></span>|
|<span data-ttu-id="5e54a-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5e54a-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="5e54a-290">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-290">Int32</span></span>|
|<span data-ttu-id="5e54a-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="5e54a-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="5e54a-292">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-292">Int16</span></span>|
|<span data-ttu-id="5e54a-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="5e54a-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="5e54a-294">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-294">Int16</span></span>|
|<span data-ttu-id="5e54a-295">POVOLENO</span><span class="sxs-lookup"><span data-stu-id="5e54a-295">NULLABLE</span></span>|<span data-ttu-id="5e54a-296">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-296">Int16</span></span>|
|<span data-ttu-id="5e54a-297">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-297">REMARKS</span></span>|<span data-ttu-id="5e54a-298">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-298">String</span></span>|
|<span data-ttu-id="5e54a-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="5e54a-299">COLUMN_DEF</span></span>|<span data-ttu-id="5e54a-300">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-300">String</span></span>|
|<span data-ttu-id="5e54a-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="5e54a-302">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-302">Int16</span></span>|
|<span data-ttu-id="5e54a-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="5e54a-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="5e54a-304">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-304">Int16</span></span>|
|<span data-ttu-id="5e54a-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5e54a-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="5e54a-306">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-306">Int32</span></span>|
|<span data-ttu-id="5e54a-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5e54a-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="5e54a-308">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-308">Int32</span></span>|
|<span data-ttu-id="5e54a-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5e54a-309">IS_NULLABLE</span></span>|<span data-ttu-id="5e54a-310">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-310">String</span></span>|
|<span data-ttu-id="5e54a-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="5e54a-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="5e54a-312">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-312">String</span></span>|
|<span data-ttu-id="5e54a-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="5e54a-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="5e54a-314">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-314">String</span></span>|
|<span data-ttu-id="5e54a-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="5e54a-316">Byte</span><span class="sxs-lookup"><span data-stu-id="5e54a-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="5e54a-317">Ovladač Microsoft Oracle ODBC</span><span class="sxs-lookup"><span data-stu-id="5e54a-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="5e54a-318">Ovladač Microsoft SQL Server Oracle ODBC podporuje kromě běžných kolekcí schémat i následující konkrétní kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="5e54a-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="5e54a-319">Tabulky</span><span class="sxs-lookup"><span data-stu-id="5e54a-319">Tables</span></span>

- <span data-ttu-id="5e54a-320">Sloupce</span><span class="sxs-lookup"><span data-stu-id="5e54a-320">Columns</span></span>

- <span data-ttu-id="5e54a-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="5e54a-321">Procedures</span></span>

- <span data-ttu-id="5e54a-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5e54a-322">ProcedureColumns</span></span>

- <span data-ttu-id="5e54a-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5e54a-323">ProcedureParameters</span></span>

- <span data-ttu-id="5e54a-324">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="5e54a-324">Views</span></span>

- <span data-ttu-id="5e54a-325">Indexy</span><span class="sxs-lookup"><span data-stu-id="5e54a-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="5e54a-326">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="5e54a-326">Tables and Views</span></span>

|<span data-ttu-id="5e54a-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-327">ColumnName</span></span>|<span data-ttu-id="5e54a-328">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5e54a-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="5e54a-330">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-330">String</span></span>|
|<span data-ttu-id="5e54a-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e54a-331">TABLE_OWNER</span></span>|<span data-ttu-id="5e54a-332">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-332">String</span></span>|
|<span data-ttu-id="5e54a-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-333">TABLE_NAME</span></span>|<span data-ttu-id="5e54a-334">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-334">String</span></span>|
|<span data-ttu-id="5e54a-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-335">TABLE_TYPE</span></span>|<span data-ttu-id="5e54a-336">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-336">String</span></span>|
|<span data-ttu-id="5e54a-337">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-337">REMARKS</span></span>|<span data-ttu-id="5e54a-338">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="5e54a-339">Sloupce</span><span class="sxs-lookup"><span data-stu-id="5e54a-339">Columns</span></span>

|<span data-ttu-id="5e54a-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-340">ColumnName</span></span>|<span data-ttu-id="5e54a-341">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5e54a-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="5e54a-343">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-343">String</span></span>|
|<span data-ttu-id="5e54a-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e54a-344">TABLE_OWNER</span></span>|<span data-ttu-id="5e54a-345">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-345">String</span></span>|
|<span data-ttu-id="5e54a-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-346">TABLE_NAME</span></span>|<span data-ttu-id="5e54a-347">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-347">String</span></span>|
|<span data-ttu-id="5e54a-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-348">COLUMN_NAME</span></span>|<span data-ttu-id="5e54a-349">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-349">String</span></span>|
|<span data-ttu-id="5e54a-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-350">DATA_TYPE</span></span>|<span data-ttu-id="5e54a-351">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-351">Int16</span></span>|
|<span data-ttu-id="5e54a-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-352">TYPE_NAME</span></span>|<span data-ttu-id="5e54a-353">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-353">String</span></span>|
|<span data-ttu-id="5e54a-354">ČÍSLIC</span><span class="sxs-lookup"><span data-stu-id="5e54a-354">PRECISION</span></span>|<span data-ttu-id="5e54a-355">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-355">Int32</span></span>|
|<span data-ttu-id="5e54a-356">ČASOVÝ</span><span class="sxs-lookup"><span data-stu-id="5e54a-356">LENGTH</span></span>|<span data-ttu-id="5e54a-357">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-357">Int32</span></span>|
|<span data-ttu-id="5e54a-358">KAPACITY</span><span class="sxs-lookup"><span data-stu-id="5e54a-358">SCALE</span></span>|<span data-ttu-id="5e54a-359">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-359">Int16</span></span>|
|<span data-ttu-id="5e54a-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="5e54a-360">RADIX</span></span>|<span data-ttu-id="5e54a-361">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-361">Int16</span></span>|
|<span data-ttu-id="5e54a-362">POVOLENO</span><span class="sxs-lookup"><span data-stu-id="5e54a-362">NULLABLE</span></span>|<span data-ttu-id="5e54a-363">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-363">Int16</span></span>|
|<span data-ttu-id="5e54a-364">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-364">REMARKS</span></span>|<span data-ttu-id="5e54a-365">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-365">String</span></span>|
|<span data-ttu-id="5e54a-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5e54a-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="5e54a-367">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="5e54a-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="5e54a-368">Procedures</span></span>

|<span data-ttu-id="5e54a-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-369">ColumnName</span></span>|<span data-ttu-id="5e54a-370">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5e54a-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="5e54a-372">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-372">String</span></span>|
|<span data-ttu-id="5e54a-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e54a-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="5e54a-374">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-374">String</span></span>|
|<span data-ttu-id="5e54a-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="5e54a-376">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-376">String</span></span>|
|<span data-ttu-id="5e54a-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="5e54a-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="5e54a-378">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-378">Int16</span></span>|
|<span data-ttu-id="5e54a-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="5e54a-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="5e54a-380">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-380">Int16</span></span>|
|<span data-ttu-id="5e54a-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="5e54a-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="5e54a-382">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-382">Int16</span></span>|
|<span data-ttu-id="5e54a-383">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-383">REMARKS</span></span>|<span data-ttu-id="5e54a-384">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-384">String</span></span>|
|<span data-ttu-id="5e54a-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5e54a-386">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="5e54a-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5e54a-387">ProcedureColumns</span></span>

|<span data-ttu-id="5e54a-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-388">ColumnName</span></span>|<span data-ttu-id="5e54a-389">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5e54a-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="5e54a-391">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-391">String</span></span>|
|<span data-ttu-id="5e54a-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e54a-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="5e54a-393">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-393">String</span></span>|
|<span data-ttu-id="5e54a-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="5e54a-395">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-395">String</span></span>|
|<span data-ttu-id="5e54a-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-396">COLUMN_NAME</span></span>|<span data-ttu-id="5e54a-397">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-397">String</span></span>|
|<span data-ttu-id="5e54a-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-398">COLUMN_TYPE</span></span>|<span data-ttu-id="5e54a-399">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-399">Int16</span></span>|
|<span data-ttu-id="5e54a-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-400">DATA_TYPE</span></span>|<span data-ttu-id="5e54a-401">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-401">Int16</span></span>|
|<span data-ttu-id="5e54a-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-402">TYPE_NAME</span></span>|<span data-ttu-id="5e54a-403">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-403">String</span></span>|
|<span data-ttu-id="5e54a-404">ČÍSLIC</span><span class="sxs-lookup"><span data-stu-id="5e54a-404">PRECISION</span></span>|<span data-ttu-id="5e54a-405">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-405">Int32</span></span>|
|<span data-ttu-id="5e54a-406">ČASOVÝ</span><span class="sxs-lookup"><span data-stu-id="5e54a-406">LENGTH</span></span>|<span data-ttu-id="5e54a-407">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-407">Int32</span></span>|
|<span data-ttu-id="5e54a-408">KAPACITY</span><span class="sxs-lookup"><span data-stu-id="5e54a-408">SCALE</span></span>|<span data-ttu-id="5e54a-409">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-409">Int16</span></span>|
|<span data-ttu-id="5e54a-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="5e54a-410">RADIX</span></span>|<span data-ttu-id="5e54a-411">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-411">Int16</span></span>|
|<span data-ttu-id="5e54a-412">POVOLENO</span><span class="sxs-lookup"><span data-stu-id="5e54a-412">NULLABLE</span></span>|<span data-ttu-id="5e54a-413">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-413">Int16</span></span>|
|<span data-ttu-id="5e54a-414">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-414">REMARKS</span></span>|<span data-ttu-id="5e54a-415">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-415">String</span></span>|
|<span data-ttu-id="5e54a-416">METODY</span><span class="sxs-lookup"><span data-stu-id="5e54a-416">OVERLOAD</span></span>|<span data-ttu-id="5e54a-417">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-417">Int32</span></span>|
|<span data-ttu-id="5e54a-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5e54a-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="5e54a-419">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="5e54a-420">Ovladač Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="5e54a-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="5e54a-421">Ovladač Microsoft Jet ODBC podporuje kromě běžných kolekcí schémat i následující konkrétní kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="5e54a-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="5e54a-422">Tabulky</span><span class="sxs-lookup"><span data-stu-id="5e54a-422">Tables</span></span>

- <span data-ttu-id="5e54a-423">Indexy</span><span class="sxs-lookup"><span data-stu-id="5e54a-423">Indexes</span></span>

- <span data-ttu-id="5e54a-424">Sloupce</span><span class="sxs-lookup"><span data-stu-id="5e54a-424">Columns</span></span>

- <span data-ttu-id="5e54a-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="5e54a-425">Procedures</span></span>

- <span data-ttu-id="5e54a-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5e54a-426">ProcedureColumns</span></span>

- <span data-ttu-id="5e54a-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5e54a-427">ProcedureParameters</span></span>

- <span data-ttu-id="5e54a-428">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="5e54a-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="5e54a-429">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="5e54a-429">Tables and Views</span></span>

|<span data-ttu-id="5e54a-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-430">ColumnName</span></span>|<span data-ttu-id="5e54a-431">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5e54a-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="5e54a-433">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-433">String</span></span>|
|<span data-ttu-id="5e54a-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e54a-434">TABLE_OWNER</span></span>|<span data-ttu-id="5e54a-435">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-435">String</span></span>|
|<span data-ttu-id="5e54a-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-436">TABLE_NAME</span></span>|<span data-ttu-id="5e54a-437">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-437">String</span></span>|
|<span data-ttu-id="5e54a-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-438">TABLE_TYPE</span></span>|<span data-ttu-id="5e54a-439">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-439">String</span></span>|
|<span data-ttu-id="5e54a-440">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-440">REMARKS</span></span>|<span data-ttu-id="5e54a-441">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="5e54a-442">Sloupce</span><span class="sxs-lookup"><span data-stu-id="5e54a-442">Columns</span></span>

|<span data-ttu-id="5e54a-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-443">ColumnName</span></span>|<span data-ttu-id="5e54a-444">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5e54a-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="5e54a-446">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-446">String</span></span>|
|<span data-ttu-id="5e54a-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e54a-447">TABLE_OWNER</span></span>|<span data-ttu-id="5e54a-448">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-448">String</span></span>|
|<span data-ttu-id="5e54a-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-449">TABLE_NAME</span></span>|<span data-ttu-id="5e54a-450">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-450">String</span></span>|
|<span data-ttu-id="5e54a-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-451">COLUMN_NAME</span></span>|<span data-ttu-id="5e54a-452">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-452">String</span></span>|
|<span data-ttu-id="5e54a-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-453">DATA_TYPE</span></span>|<span data-ttu-id="5e54a-454">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-454">Int16</span></span>|
|<span data-ttu-id="5e54a-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-455">TYPE_NAME</span></span>|<span data-ttu-id="5e54a-456">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-456">String</span></span>|
|<span data-ttu-id="5e54a-457">ČÍSLIC</span><span class="sxs-lookup"><span data-stu-id="5e54a-457">PRECISION</span></span>|<span data-ttu-id="5e54a-458">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-458">Int32</span></span>|
|<span data-ttu-id="5e54a-459">ČASOVÝ</span><span class="sxs-lookup"><span data-stu-id="5e54a-459">LENGTH</span></span>|<span data-ttu-id="5e54a-460">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-460">Int32</span></span>|
|<span data-ttu-id="5e54a-461">KAPACITY</span><span class="sxs-lookup"><span data-stu-id="5e54a-461">SCALE</span></span>|<span data-ttu-id="5e54a-462">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-462">Int16</span></span>|
|<span data-ttu-id="5e54a-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="5e54a-463">RADIX</span></span>|<span data-ttu-id="5e54a-464">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-464">Int16</span></span>|
|<span data-ttu-id="5e54a-465">POVOLENO</span><span class="sxs-lookup"><span data-stu-id="5e54a-465">NULLABLE</span></span>|<span data-ttu-id="5e54a-466">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-466">Int16</span></span>|
|<span data-ttu-id="5e54a-467">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-467">REMARKS</span></span>|<span data-ttu-id="5e54a-468">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-468">String</span></span>|
|<span data-ttu-id="5e54a-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5e54a-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="5e54a-470">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="5e54a-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="5e54a-471">Procedures</span></span>

|<span data-ttu-id="5e54a-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-472">ColumnName</span></span>|<span data-ttu-id="5e54a-473">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5e54a-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="5e54a-475">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-475">String</span></span>|
|<span data-ttu-id="5e54a-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e54a-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="5e54a-477">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-477">String</span></span>|
|<span data-ttu-id="5e54a-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="5e54a-479">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-479">String</span></span>|
|<span data-ttu-id="5e54a-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="5e54a-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="5e54a-481">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-481">Int16</span></span>|
|<span data-ttu-id="5e54a-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="5e54a-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="5e54a-483">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-483">Int16</span></span>|
|<span data-ttu-id="5e54a-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="5e54a-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="5e54a-485">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-485">Int16</span></span>|
|<span data-ttu-id="5e54a-486">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-486">REMARKS</span></span>|<span data-ttu-id="5e54a-487">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-487">String</span></span>|
|<span data-ttu-id="5e54a-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="5e54a-489">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="5e54a-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="5e54a-490">ProcedureColumns</span></span>

|<span data-ttu-id="5e54a-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-491">ColumnName</span></span>|<span data-ttu-id="5e54a-492">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="5e54a-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="5e54a-494">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-494">String</span></span>|
|<span data-ttu-id="5e54a-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e54a-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="5e54a-496">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-496">String</span></span>|
|<span data-ttu-id="5e54a-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="5e54a-498">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-498">String</span></span>|
|<span data-ttu-id="5e54a-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-499">COLUMN_NAME</span></span>|<span data-ttu-id="5e54a-500">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-500">String</span></span>|
|<span data-ttu-id="5e54a-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-501">COLUMN_TYPE</span></span>|<span data-ttu-id="5e54a-502">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-502">Int16</span></span>|
|<span data-ttu-id="5e54a-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-503">DATA_TYPE</span></span>|<span data-ttu-id="5e54a-504">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-504">Int16</span></span>|
|<span data-ttu-id="5e54a-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-505">TYPE_NAME</span></span>|<span data-ttu-id="5e54a-506">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-506">String</span></span>|
|<span data-ttu-id="5e54a-507">ČÍSLIC</span><span class="sxs-lookup"><span data-stu-id="5e54a-507">PRECISION</span></span>|<span data-ttu-id="5e54a-508">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-508">Int32</span></span>|
|<span data-ttu-id="5e54a-509">ČASOVÝ</span><span class="sxs-lookup"><span data-stu-id="5e54a-509">LENGTH</span></span>|<span data-ttu-id="5e54a-510">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-510">Int32</span></span>|
|<span data-ttu-id="5e54a-511">KAPACITY</span><span class="sxs-lookup"><span data-stu-id="5e54a-511">SCALE</span></span>|<span data-ttu-id="5e54a-512">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-512">Int16</span></span>|
|<span data-ttu-id="5e54a-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="5e54a-513">RADIX</span></span>|<span data-ttu-id="5e54a-514">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-514">Int16</span></span>|
|<span data-ttu-id="5e54a-515">POVOLENO</span><span class="sxs-lookup"><span data-stu-id="5e54a-515">NULLABLE</span></span>|<span data-ttu-id="5e54a-516">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-516">Int16</span></span>|
|<span data-ttu-id="5e54a-517">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-517">REMARKS</span></span>|<span data-ttu-id="5e54a-518">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-518">String</span></span>|
|<span data-ttu-id="5e54a-519">METODY</span><span class="sxs-lookup"><span data-stu-id="5e54a-519">OVERLOAD</span></span>|<span data-ttu-id="5e54a-520">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-520">Int32</span></span>|
|<span data-ttu-id="5e54a-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5e54a-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="5e54a-522">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="5e54a-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="5e54a-523">ProcedureParameters</span></span>

|<span data-ttu-id="5e54a-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="5e54a-524">ColumnName</span></span>|<span data-ttu-id="5e54a-525">DataType</span><span class="sxs-lookup"><span data-stu-id="5e54a-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="5e54a-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="5e54a-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="5e54a-527">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-527">String</span></span>|
|<span data-ttu-id="5e54a-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="5e54a-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="5e54a-529">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-529">String</span></span>|
|<span data-ttu-id="5e54a-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="5e54a-531">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-531">String</span></span>|
|<span data-ttu-id="5e54a-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-532">COLUMN_NAME</span></span>|<span data-ttu-id="5e54a-533">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-533">String</span></span>|
|<span data-ttu-id="5e54a-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-534">COLUMN_TYPE</span></span>|<span data-ttu-id="5e54a-535">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-535">Int16</span></span>|
|<span data-ttu-id="5e54a-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-536">DATA_TYPE</span></span>|<span data-ttu-id="5e54a-537">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-537">Int16</span></span>|
|<span data-ttu-id="5e54a-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="5e54a-538">TYPE_NAME</span></span>|<span data-ttu-id="5e54a-539">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-539">String</span></span>|
|<span data-ttu-id="5e54a-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="5e54a-540">COLUMN_SIZE</span></span>|<span data-ttu-id="5e54a-541">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-541">Int32</span></span>|
|<span data-ttu-id="5e54a-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5e54a-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="5e54a-543">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-543">Int32</span></span>|
|<span data-ttu-id="5e54a-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="5e54a-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="5e54a-545">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-545">Int16</span></span>|
|<span data-ttu-id="5e54a-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="5e54a-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="5e54a-547">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-547">Int16</span></span>|
|<span data-ttu-id="5e54a-548">POVOLENO</span><span class="sxs-lookup"><span data-stu-id="5e54a-548">NULLABLE</span></span>|<span data-ttu-id="5e54a-549">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-549">Int16</span></span>|
|<span data-ttu-id="5e54a-550">MARK</span><span class="sxs-lookup"><span data-stu-id="5e54a-550">REMARKS</span></span>|<span data-ttu-id="5e54a-551">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-551">String</span></span>|
|<span data-ttu-id="5e54a-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="5e54a-552">COLUMN_DEF</span></span>|<span data-ttu-id="5e54a-553">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-553">String</span></span>|
|<span data-ttu-id="5e54a-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="5e54a-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="5e54a-555">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-555">Int16</span></span>|
|<span data-ttu-id="5e54a-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="5e54a-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="5e54a-557">Int16</span><span class="sxs-lookup"><span data-stu-id="5e54a-557">Int16</span></span>|
|<span data-ttu-id="5e54a-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="5e54a-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="5e54a-559">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-559">Int32</span></span>|
|<span data-ttu-id="5e54a-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="5e54a-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="5e54a-561">Int32</span><span class="sxs-lookup"><span data-stu-id="5e54a-561">Int32</span></span>|
|<span data-ttu-id="5e54a-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="5e54a-562">IS_NULLABLE</span></span>|<span data-ttu-id="5e54a-563">String</span><span class="sxs-lookup"><span data-stu-id="5e54a-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="5e54a-564">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e54a-564">See also</span></span>

- [<span data-ttu-id="5e54a-565">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5e54a-565">ADO.NET Overview</span></span>](ado-net-overview.md)
